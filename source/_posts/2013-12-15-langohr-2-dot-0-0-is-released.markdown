---
layout: post
title: "Langohr 2.0.0 is released"
date: 2013-12-15 21:12
comments: false
categories:
  - langohr
  - rabbitmq
  - releases
---

## TL;DR

Langohr is a [Clojure RabbitMQ client](http://clojurerabbitmq.info) that embraces [AMQP 0.9.1 Model](http://www.rabbitmq.com/tutorials/amqp-concepts.html).

`2.0.0` is a major release that introduces automatic topology (queues,
exchanges, bindings, and consumers) recovery.


## Making Automatic Connection Recovery More Awesome

Langohr `1.7.0` supports automatic recovery of connections and channels
when network connectivity fails. However, recovery of queues, exchanges, bindings
and consumers was up to developers. In most cases, topology recovery
consists of a few straightforward steps:

 * Re-declare queues
 * Re-declare exchanges
 * Re-establish bindings
 * Re-register consumers

Langohr 2.0 provides a feature that performs those steps automatically.
Every channel now tracks the entities declared on it and re-declares them
after recovery. It's possible to disable this feature and perform manual
recovery, just like before.

For many applications, recovery from network and node failures will
now be almost effortless. Give it a try and [let us
know](mailto:contact@clojurewerkz.org) how it goes!


## Changes between Langohr 1.7.0 and 2.0.0

### Topology (Queues, Exchanges, Bindings, Consumers) Recovery

Connection recovery now supports entity recovery. Queues, exchanges,
bindings and consumers can be recovered automatically after channel
recovery. This feature is enabled by default and can be disabled
by setting the `:automatically-recover-topology` option to `false`.

### :requested-channel-max Connection Option

`:requested-channel-max` is a new option accepted by
`langohr.core/connect` that configures how many channels
this connection may have. The limit is enforced on the client
side. `0` means "no limit" and is the default.

Contributed by Glophindale.

### langohr.queue/empty?

`langohr.queue/empty?` is a new function that returns true if provided
queue is empty (has 0 messages ready):

``` clojure
(require '[langohr.queue :as lq])

(lq/empty? ch "a.queue")
;= true
```


### langohr.core/add-shutdown-listener

`langohr.core/add-shutdown-listener` is a helper function that
reifies and registers a shutdown signal listener on a connection.

### langohr.core/add-blocked-listener

`langohr.core/add-blocked-listener` is a helper function that
reifies and registers a `connection.blocked` and `connection.unblocked`
listener on a connection.



## Change Log

[Langohr change
log](https://github.com/michaelklishin/langohr/blob/master/ChangeLog.md)
is available on GitHub.


## Langohr is a ClojureWerkz Project

[Langohr](http://clojurerabbitmq.info) is part of the [group of
libraries known as ClojureWerkz](http://clojurewerkz.org), together
with

 * [Elastisch](http://clojureelasticsearch.info), a minimalistic well documented Clojure client for ElasticSearch
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client built around CQL 3.0
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Langohr, you may also like [our other
projects](http://clojurewerkz.org).

Let us know what you think [on
Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing
list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the
[ClojureWerkz](http://clojurewerkz.org) Team
