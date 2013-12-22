---
layout: post
title: "Langohr 2.0.1 is released"
date: 2013-12-22 12:52
comments: false
categories:
  - langohr
  - rabbitmq
  - releases
---

## TL;DR

Langohr is a small [Clojure RabbitMQ client](http://clojurerabbitmq.info).

`2.0.1` is a bug fix release.


## Changes between Langohr 2.0.0 and 2.0.1

### No Zombie Bindings After Recovery

Langohr now correctly removes bindings from the list of
bindings to recover when a binding is removed using `queue.unbind`
or `exchange.unbind`.


## Change Log

[Langohr change
log](https://github.com/michaelklishin/langohr/blob/2.0.x-stable/ChangeLog.md)
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
