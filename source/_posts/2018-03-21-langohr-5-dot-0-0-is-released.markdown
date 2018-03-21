---
layout: post
title: "Langohr 5.0.0 is released"
date: 2018-03-21 12:18:11 +0300
comments: false
categories:
  - langohr
  - rabbitmq
  - releases
---

## TL;DR

Langohr is a small [Clojure RabbitMQ client](http://clojurerabbitmq.info).

`5.0.0` is a release that upgrades Java client dependency to `5.x.`.


## Changes in 5.0.0

### RabbitMQ Java Client Upgrade

RabbitMQ Java client dependency has been updated to `5.x`.

### JDK 8 is Now Required

RabbitMQ Java client 5.x requires JDK 8. It's a good chance
to drop support for older JDKs in Langohr. Langohr `4.x` continues
to use a JDK 6 and 7-compatible version of the Java client.

### Queueing/Blocking Consumers are Removed

RabbitMQ Java client 5.0 removed a long deprecated queueing consumer
abstraction that used an internal `j.u.c` queue for deliveries and acted as
an iterator. That consumer implementation never supported automatic connection
recovery and isn't necessary with modern consumer operation dispatch pool.

Langohr follows suit and removes the following functions based on the `QueueingConsumer`:

 * `langohr.basic/blocking-subscribe`
 * `langohr.consumers/create-queueing`
 * `langohr.consumers/deliveries-seq`

`langohr.consumers/deliveries-seq` may be reintroduced in the future if a reasonable
imlementation for it comes to mind/is contributed.

### clj-http Upgrade

clj-http dependency has been updated to `3.8.x`.


## Change Log

[Langohr change log](https://github.com/michaelklishin/langohr/blob/master/ChangeLog.md)
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

## About The Author

[Michael](http://twitter.com/michaelklishin) on behalf of the
[ClojureWerkz](http://clojurewerkz.org) Team
