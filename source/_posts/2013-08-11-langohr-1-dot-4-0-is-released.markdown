---
layout: post
title: "Langohr 1.4.0 is released"
date: 2013-08-11 22:17
comments: false
categories:
  - langohr
  - releases
---

## TL;DR

Langohr is a [Clojure RabbitMQ client](http://clojurerabbitmq.info) that embraces [AMQP 0.9.1 Model](http://www.rabbitmq.com/tutorials/amqp-concepts.html).

`1.4.0` is a minor feature release that primarily improves pre-`1.1.0` version compatibility
and connection recovery features.


## Changes between Langohr 1.3.0 and 1.4.0

### Network Recovery Callbacks on Connections and Channels

They can be used to re-declare necessary entities using `langohr.core/on-recovery`:

``` clojure
(langohr.core/on-recovery conn (fn [conn] (comment ...)))

(langohr.core/on-recovery ch   (fn [ch] (comment ...)))
```

Unlike OO clients that represent queues and
exchanges as objects, Langohr cannot be more
aggressive about redeclaring entities during
connection recovery.


## Changes between Langohr 1.2.0 and 1.3.0

## Re-introduce langohr.consumers/create-queueing

The function creates a `QueueingConsumer` instance and is very similar
to `langohr.consumers/create-default` in purpose.

Sometimes combining a queueing consumer with
`langohr.consumers/deliveries-seq` is the best way to express a
problem.

### Rename langoh.consumers/consumers-seq to langoh.consumers/deliveries-seq, make it public

`langoh.consumers/deliveries-seq` is a function that turns a `QueueingConsumer` instance
into a lazy sequence of deliveries.

### Use :executor During Connection Recovery

Connection recovery after network failure will now respect the `:executor`
option.


## Changes between Langohr 1.1.0 and 1.2.0

### Langohr Again Uses RabbitMQ Java Client Interfaces

Langohr's implementation of connection and channel now implements
RabbitMQ Java client's interfaces for connection and channel.



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
