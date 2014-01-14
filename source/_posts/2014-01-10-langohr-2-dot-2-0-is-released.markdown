---
layout: post
title: "Langohr 2.2.0 is released"
date: 2014-01-10 20:14
comments: false
categories:
  - langohr
  - releases
  - rabbitmq
---

## TL;DR

Langohr is a small [Clojure RabbitMQ client](http://clojurerabbitmq.info).

`2.2.0` is a usability improvement release.


## Changes between Langohr 2.1.x and 2.2.0

### Automatic Topology Recovery Tracks Entities Per Connection

Automatic topology recovery now tracks entities (exchanges,
queues, bindings, and consumers) per connection. This makes
it possible to, say, declare an exchange on one channel, delete
it on another channel and not have it reappear.

Suggested by Jonathan Halterman.


### RabbitMQ Java Client Upgrade

RabbitMQ Java client dependency has been updated to `3.2.2`.

### clj-http Upgrade

clj-http dependency has been updated to `0.7.8`.

### Cheshire Upgrade

Cheshire dependency has been updated to `5.3.1`.



## Change Log

[Langohr change
log](https://github.com/michaelklishin/langohr/blob/2.2.x-stable/ChangeLog.md)
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
