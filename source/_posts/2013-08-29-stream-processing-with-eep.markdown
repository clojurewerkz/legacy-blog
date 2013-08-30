---
layout: post
title: "Introducing  EEP, a Stream Processing Library"
date: 2013-08-29 09:23
comments: false
categories:
  - eep
  - releases
---

## Drinking From The Data Firehose

If you work with data a lot, and you have a lot of it, it becomes
nearly impossible to process the entire corpus in one run. Sometimes
you simply can't do that at all, since the data is coming in form of
events.  Moreover, as your codebase grows, you'll be forced to create
a library that allows you get most of routing out of the way, so that
you could pay more attention to details rather than to grasp the entire
flow.

There's been lot of progress on this subject lately in the Clojure
community.  Prismatic folks released their processing library,
[Graph](https://github.com/Prismatic/plumbing). Kyle Kingsbury created
[Riemann](https://github.com/aphyr/riemann) that uses a similar
approach internally. Zach Tellman, creator of Aleph, released
[Lamina](https://github.com/ztellman/lamina) for working with streams,
a couple of years ago.
[Eventsourced](https://github.com/eligosource/eventsourced),
[Pipes](http://pipes.tinkerpop.com) from Tinkerpop, and
[Storm](http://github.com/nathanmarz/storm) by Nathan Marz can also
be counted as good example.

The basic idea remains the same. You have a stream of data coming in
in form of events. You build a topology of functions that broadcast,
transform, filter, aggregate or save state of said events. At any
given point in time you can know the intermediate result of
calculation, in case when stream of events is being fetched from some
data source, or can get results interactively (real-time, 
yo), and react to the system behavior.

After trying pretty much same approach out for quite some things, it
did work quite well. Of course, depending on the required throughput
my approach may be not exactly what you want to use in your production
system, but most likely the interface will still be similar to the
alternatives, even though implementation details will vary.

Today we are release our own library into this melting pot of JVM-based
stream processing projects.

## Enter EEP

[EEP](https://github.com/clojurewerkz/eep) is our own young entrant to this space.

When we've first started investigating __state of the art__ of event processing,
intuitive choices for inspiration were Erlang (`gen_event`) and
Node.js (don't judge!). They certainly
have very different approaches to concurrency but there are similarities.

In [gen_event](http://www.erlang.org/doc/man/gen_event.html), two
functions that are used more often than others are
`gen_event:add_handler` and `gen_event:notify`. The former subscribes you to
an occuring event, the latter sends events to the emitter, which dispatches
them to the handler. [Node.js](http://nodejs.org/api/events.html) approach is
very similar: multiple handlers per event type, routed on emission.

Next we will briefly cover EEP concepts and demonstrate what it feels
like to use it with some code examples.


## Core concepts

Core concepts in EEP are:

  * `Emitter` is responsible for handler registration and event
    routing. It holds everything together.

  * `Event` is a tuple dispatched by world into the emitter. Event is an
    arbitrary tuple of user-defined structure. There's no validation
    provided internally for structure.

  * `Event Type` is a unique event type identifier, used for routing. It can
    be number, symbol, keyword, string or anything else. All the events
    coming into `Emitter` have type associated with them.

  * `Handler` is a function and optional state attached to it. Function is a
    callback, executed whenever `Event Type` is matched for the
    event. Single handler can be used for multiple `Event Types`, but
    `Event Type` can only have one `Handler` at a time.


## Building Data Flows

Now, with these building blocks we can go ahead and start building
processing graphs. For that, we need to define several types of handlers
that are aware of what data looks like.

   * `filter` receives events of a certain type, and forwards ones
     for which `filter-fn` returns `true` to one or more other handlers

   * `splitter` receives events of a certain type, and dispatches them
     to type returned by predicate function. For example, you can split
     stream of integers to even and odd ones and process them down the
     pipeline differently.

   * `transformer` defines a transformer that gets typed tuples, applies
     transformation function to each one of them and forwards them to
     one or more other handlers. It's similar to applying `map` to
     elements of a list, except for function is applied to stream of data.

   * `aggregator` is initialized with initial value, then gets events of
     a certain type and aggregates state by applying aggregate function to
     current state and an incoming event. It's similar to `reduce`
     function in Clojure, except for it's applied to the stream of data.

   * `multicast` receives events of a certain type and broadcasts them
     to several handlers with different types. For example, whenever an
     alert is received, you may want to send notifications via email,
     IRC, Jabber and append event to the log file.

   * `observer` receives events of a certain type and runs function
     (potentially with side-effects) on each one of them.

   * `buffer` receives events of a certain type and stores them in a
     circular buffer with given capacity. As soon as capacity is
     reached, it distributes them to several other handlers.

   * `rollup` acts in a manner similar to buffer, except for it's
     time-bound but not capacity-bound, so whenever a time period is
     reached, it dispatches all the events to several other handlers.

Let's take a closer look at an example of stream processing. For
instance, you have a discrete stream of events coming from the web
servers, that hold information about page loads on your
website. Interesting infromation to monitor would be:

  * host (where the page load occured)
  * response code (HTTP status of the response)
  * user agent infromation
  * response duration
  * url of the response

From that single payload type you can already yield an incredible amount
of information, for example

  * slowest/fastest response time
  * last 20 response times
  * total number of responses (per given amount of time)
  * response number breakdown by status code
  * hottest URLs on the website (page loads breakdown by url)
  * user agent breakdown
  * count only 404s

If you do it in the most straightforward way, you will end up with lots
of ad-hoc code, that is related to routing: metrics that are related to
response time only need response time, you'll need to have buffers for
rollups that will aggregate data for a certain period and stream it to
next computation unit and so on.

We went through many use-cases that are related to discrete data
aggregation and worked out several entities that will help to create
calculation topologies. Besides that, you'll need a queue that will have
some build-in routing capabilities and will manage buffered aggregation,
filters, stream data down to several handlers and many other,
not-so-obvious things.

Now, we'll need to declare the metrics we want to aggregate on. In order
to make our processing graph more reusable, we'll separate metric
retrieval from metric calculation. This way, we'll be able to reuse same
aggregate function for several types of metrics and will be able to
achieve desired result by providing appropriate routing.

```clj
(def emitter (new-emitter))

;; Redistribute an event to all transformers and aggregators
(defmulticast emitter :page-load [:total-request-count
                                  :load-time-metrics
                                  :status-code-metrics
                                  :user-agent-metrics
                                  :url-metrics])
```

Now, let's define transformers that receive a complete event, take a
single field out of it and redistribute it further down:

```clj
;; Take only :load-time for metrics related to load time
(deftransformer emitter :load-time-metrics :load-time [:load-time-slowest :load-time-fastest :load-times-last-20])

;; Take only :status for metrics related to status code
(deftransformer emitter :status-code-metrics :status :count-by-status-code)

;; Take only :user-agent for metrics related to user agent
(deftransformer emitter :user-agent-metrics :user-agent :count-by-user-agent)

;; Take only :url for metrics related to url
(deftransformer emitter :url-metrics :url :count-by-url)
```

Now, we can define our aggregate functions:

```clj
;; Define an counter aggregator for all requests
(defaggregator emitter :total-request-count (fn [acc _] (inc acc)) 0)

;; Preserve only slowest load time
(defaggregator emitter :load-time-slowest (fn [previous current]
                                            (if (and previous (< previous current))
                                              previous
                                              current)) nil)
;; Preserve only fastest load time
(defaggregator emitter :load-time-fastest (fn [previous current]
                                            (if (and previous (> previous current))
                                              previous
                                              current)) nil)

(let [count-aggregate (fn [acc metric]
                        (assoc acc metric (inc (get acc metric 0))))]
  ;; Aggregate counts by status code
  (defaggregator emitter :count-by-status-code count-aggregate {})

  ;; Aggregate counts by user agent code
  (defaggregator emitter :count-by-user-agent count-aggregate {})

  ;; Aggregate counts by user url
  (defaggregator emitter :count-by-url count-aggregate {}))

;; Define a buffer for last 20 events
(defbuffer emitter :load-times-last-20 20)
```

Now our graph is ready, we can visualize it:

![Graph Visualisation](/images/posts/rhizome-graph.png)

In order to pump some data into the processing graph, let's generate some random events:

```clj
(defn rand-between
  "Generates a random number between two points"
  [start end] (+ start (rand-int (- end start))))

(def hosts ["host01" "host02" "host03" "host04" "host05"])
(def urls ["/url01" "/url02" "/url03" "/url04" "/url05"])
(def user-agents ["Chrome" "Mozilla" "Safari" "Firefox"])

(def status-codes [200 404 500 302])

(defn gen-events
  "Generates an infinite stream of random data"
  ([]
     (gen-events [] 0))
  ([c i]
     (lazy-cat c (gen-events
                  [{:event_id i
                    :host        (get hosts (rand-between 0 (count hosts)))
                    :status      (get status-codes (rand-between 0 (count status-codes)))
                    :url         (get urls (rand-between 0 (count urls)))
                    :user-agent  (get user-agents (rand-between 0 (count user-agents)))
                    :load-time   (rand-between 300 500)}]
                  (inc i)))))


(defn median
  "Calculates median for given array of numbers"
  [data]
  (let [sorted (sort data)
        n (count data)
        i (bit-shift-right n 1)]
    (if (even? n)
      (/ (+ (nth sorted (dec i)) (nth sorted i)) 2)
      (nth sorted (bit-shift-right n 1)))))
```

And pump data to the emitter:

```clj
(doseq [event (take 20000 (gen-events))]
  (notify emitter :page-load event))

(println "Total request count: " (state (get-handler emitter :total-request-count)))
(println "Count by url:" (state (get-handler emitter :count-by-url)))
(println "Count by user agent:" (state (get-handler emitter :count-by-user-agent)))
(println "Count by user status:" (state (get-handler emitter :count-by-status-code)))
(println "Fastest load time:" (state (get-handler emitter :load-time-fastest)))
(println "Slowest load time:" (state (get-handler emitter :load-time-slowest)))
(println "Last 20 load times:" (state (get-handler emitter :load-times-last-20)))
(println "Median of fast 20 load times:" (float (median (state (get-handler emitter :load-times-last-20)))))
```


## Why Stream Processing

There're many advantages of using such an approach for data
processing. First of all, you whenever you're working with a stream,
you can have latest data available at all times.  There's no need to
go through an entire corpus of data, only get the state of the
handlers of your interest.

Every handler is reusable, and you can generate graphs in such a way, there's not a single
entrypoint to each handler, but there're several ones. If internal EEP handlers are not
enough for you, you can always reuse `IHandler` protocol and extend it with any other handler
of your preference, that would give you an ability to have sliding, tumbling, monotonic windows,
different types of buffers, custom aggregators and so on.


## What You Can Do With It

Event streams are very common in every system. One application that's been quite popular
in recent years is "logs as data" processed as a stream. Every production system produces
a stream of events and it becomes increasingly obvious to both engineers and business
owners alike that tapping into that data can bring a lot of benefits.

To make this more useful, you can use stream processing libraries such
as EEP to propagate events to mobile and Web clients, publish them to
other apps using messaging technologies such as RabbitMQ, generate
alerts and much more.

EEP is a generic project that can be used in a wide range of cases.


## Enter Meltdown

Initial implementation of EEP was based on thread pools, and was
functioning reasonably well but after some research we decided to take
a look if we can use ring buffer abstraction from
[Disruptor](https://github.com/LMAX-Exchange/disruptor). After several
interactions we ended up using
[Reactor](http://blog.springsource.org/2013/05/13/reactor-a-foundation-for-asynchronous-applications-on-the-jvm/), a new event-driven
programming framework from [Pivotal](http://gopivotal.com). It was a
game-changer. EEP got way faster, routing got so much easier (and much
faster, too).

Our Clojure interface to Reactor is a separate library, creatively
named [Meltdown](https://github.com/clojurewerkz/meltdown). Now you can deploy a meltdown into production!

We will cover Meltdown in more details in a separate blog post.


## (Some) Future Plans

We're working hard to bring a good support for numerical analysis and good set of statistical
functions to be available at your fingertips right in EEP. You can watch our progress [on GitHub](http://github.com/clojurewerkz) and follow the news [on Twitter @clojurewerkz](http://twitter.com/clojurewerkz).


## Monger is a ClojureWerkz Project

[EEP](http://github.com/clojurewerkz/eep) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client built around CQL
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like EEP, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[@ifesdjeen](http://twitter.com/ifesdjeen) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
