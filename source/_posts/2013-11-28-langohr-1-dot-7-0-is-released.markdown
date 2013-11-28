---
layout: post
title: "Langohr 1.7.0 is released"
date: 2013-11-28 18:59
comments: false
categories:
  - langohr
  - releases
---

## TL;DR

Langohr is a [Clojure RabbitMQ client](http://clojurerabbitmq.info) that embraces [AMQP 0.9.1 Model](http://www.rabbitmq.com/tutorials/amqp-concepts.html).

`1.7.0` is primarily a bug fix release.


## Changes between Langohr 1.6.0 and 1.7.0

### RabbitMQ Java Client Upgrade

RabbitMQ Java client dependency has been updated to `3.2.1`.


### Automatic Recovery Improvements

Langohr will now make sure to handle network I/O-related exceptions
during recovery and reconnect every N seconds.

[The following code
example](https://github.com/clojurewerkz/langohr.examples/blob/master/src/clojure/clojurewerkz/langohr/examples/recovery/example1.clj)
can be used to test connection recovery. Either restart RabbitMQ or
close a connection using [Management
UI](http://rabbitmq.com/management.html) to test drive it.



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
