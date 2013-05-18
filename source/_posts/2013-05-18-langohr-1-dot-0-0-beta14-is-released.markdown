---
layout: post
title: "Langohr 1.0.0-beta14 is released"
date: 2013-05-18 16:20
comments: false
categories:
  - langohr
  - releases
---

## TL;DR

Langohr is a [Clojure RabbitMQ client](http://clojurerabbitmq.info) that embraces [AMQP 0.9.1 Model](http://www.rabbitmq.com/tutorials/amqp-concepts.html).

`1.0.0-beta14` is a development milestone release that includes a few minor features,
mostly around error handling and recovery.


## Changes between Langohr 1.0.0-beta13 and 1.0.0-beta14

### Queueing Consumers

In its early days, Langohr has been using `QueueingConsumer` for `langohr.queue/subscribe`.
It was later replaced by a `DefaultConsumer` implementation.

The key difference between the two is that

 * `QueueingConsumer` blocks the caller
 * with `QueueingConsumer`, deliveries are typically processed in the same thread

This implementation has pros and cons. As such, an implementation on top of
`QueueingConsumer` is back with `langohr.consumers/blocking-subscribe` which is
identical to `langohr.consumers/subscribe` in the signature but blocks the caller.

In addition, `langohr.consumers/ack-unless-exception` is a new convenience function
that takes a delivery handler fn and will return a new function
that explicitly acks deliveries unless an exception was raised by the original handler:

``` clojure
(require '[langohr.consumers :as lc])
(require '[langohr.basic     :as lb])

(let [f  (fn [metadata payload]
           (comment "Message delivery handler"))
      f' (lc/ack-unless-exception f)]
  (lb/consume ch q (lc/create-default :handle-delivery-fn f'))
```

Contributed by Ian Eure.

### Shutdown Signal Functions

Several new functions in `langohr.shutdown` aid with shutdown signals:

 * `langohr.shutdown/initiated-by-application?`
 * `langohr.shutdown/initiated-by-broker?`
 * `langohr.shutdown/reason-of`
 * `langohr.shutdown/channel-of`
 * `langohr.shutdown/connection-of`

### Clojure 1.5 By Default

Langohr now depends on `org.clojure/clojure` version `1.5.1`. It is
still compatible with Clojure 1.3 and if your `project.clj` depends on
a different version, it will be used, but 1.5 is the default now.

We encourage all users to upgrade to 1.5, it is a drop-in replacement
for the majority of projects out there.



## Change Log

[Langohr change log](https://github.com/michaelklishin/langohr/blob/master/ChangeLog.md) is available on GitHub.


## Langohr is a ClojureWerkz Project

[Langohr](http://clojurerabbitmq.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Elastisch](http://clojureelasticsearch.info), a minimalistic well documented Clojure client for ElasticSearch
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Langohr, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
