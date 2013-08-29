---
layout: post
title: "Stream Processing with EEP"
date: 2013-08-29 09:23
comments: true
categories:
---

If you're working with data a lot, quite soon it becomes close to
impossible to process an entire corpus in one run, or you simply can't
do that, since data is coming in form of events / tuples and you perform
analysis based on the calculations. Moreover, with growth of processing
codebase you're creating some kind of framework that allows you get most
of routing out of the way, so that you could pay more attention to
details rather than to grasp an entire flow at a time.

There's a lot of progress on this subject lately. Prismatic guys
released their processing library,
[Graph](https://github.com/Prismatic/plumbing), Zach Tellman, creator of
Aleph, made [Lamina](https://github.com/ztellman/lamina) that helps you
to work with streams and gives you some abstractions, Kyle Kingsbury
created [Riemann](https://github.com/aphyr/riemann), that implements
similar approach internally,
[Eventsourced](https://github.com/eligosource/eventsourced) is another
example, [Pipes](pipes.tinkerpop.com) from Tinkerpop,
[Storm](github.com/nathanmarz/storm) by Nathan Marz and many more
examples.

Basic idea remains the same. You have a stream of data coming in in form
of events. You build a topology of functions that broadcast, transform,
filter, aggregate or save state of tuples that are going through. This
way at any given point in time you can know the intermediate result of
calculation, in case when stream of events is being fetched from some
data source, or can get results interactively (some may say real-time
yo), and react to the system behavior.

After trying pretty much same approach out for quite some things, it did
work quite well.  Of course, depending on the required throughput my
approach may be not exactly what you want to use in your production
system, but most likely interface will still remain quite similar, even
though implementation details will have pretty much nothing in common.

# Enter EEP

When we've first started investigating __state of art__ of event processing,
intuitive choices for inspiration were Erlang (gen_event) and
Node.js. Don't try to judge strictly here.  Of course, they certainly
take absolutely different approach to concurrency, but emission
part looks quite similar.

In [gen_event](http://www.erlang.org/doc/man/gen_event.html) two
functions that are used more often than others are
`gen_event:add_handler` and `gen_event:notify`. Former subscribes you to
an occuring event, latter sends event to the emitter, which dispatches
it according to the
handler. [Node.js](http://nodejs.org/api/events.html) approach is
extremely similar: multiple handlers per event type, routed on emission.

Initial implementation of EEP was based on `ThreadPoolExecutor`, and was
functioning quite well, but after some research we decided to take a
look if we can use `RingBuffer` from
[Disruptor](https://github.com/LMAX-Exchange/disruptor), and after
several interactions we ended up using
[Reactor](https://github.com/reactor/reactor), written by SpringSource/
Pivotal engineers, and it became a game-changer. It got way faster, routing
got so much easier (and much faster, too, since internal Reactor routing is using
caching registry, that works with L1 Cache and read/write reentrant locks).

Reactor turned out to use same exact approach, and migration (after
spelling out everything reactor-related in Clojure) didn't take long.

## Core concepts

Core concepts of EEP are:

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

## Handler types

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

There're many advantages of using such an approach for data processing. First of all, you
whenever you're working with a stream, you can have latest data available at all times.
There's no need to go through an entire corpus of data, only get the state of the handlers
of your interest.

This post is not about math and statistics, it's about data processing, and even though there
were no examples of more complex statistical and analytical functions given, you can use
same exact approach for anomaly detection, trend analysis, predictions, comparing current
data with historical data points and much more

For interactivity, you can use websockets, create dashboards, push data to the mobile clients,
generate email alerts and much more.

Every handler is reusable, and you can generate graphs in such a way, there's not a single
entrypoint to each handler, but there're several ones. If internal EEP handlers are not
enough for you, you can always reuse `IHandler` protocol and extend it with any other handler
of your preference, that would give you an ability to have sliding, tumbling, monotonic windows,
different types of buffers, custom aggregators and so on.

We're working hard to bring a good support for numerical analysis and good set of statistical
functions to be available at your fingertips right in EEP, watch project progress for more information
and stay tuned for all the updates on [@clojurewerkz](http://twitter.com/clojurewerkz)

If you like it, you can start using EEP already! Go grab it [on GitHub](http://github.com/clojurewerkz/eep)
