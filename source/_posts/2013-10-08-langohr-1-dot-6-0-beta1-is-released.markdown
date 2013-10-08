---
layout: post
title: "Langohr 1.6.0-beta1 is released"
date: 2013-10-08 21:44
comments: false
categories:
  - langohr
  - releases
---

## TL;DR

Langohr is a [Clojure RabbitMQ client](http://clojurerabbitmq.info) that embraces [AMQP 0.9.1 Model](http://www.rabbitmq.com/tutorials/amqp-concepts.html).

`1.6.0-beta1` is a development milestone release that includes
improvements to automatic connection recovery.


## Changes between Langohr 1.5.0 and 1.6.0

### Automatic Recovery Improvements

Connections will only be recovered if shutdown was not application-initiated.

Contributed by Steffen Dienst.


### Support Update

Langohr now depends on ClojureWerkz Support `0.20.0`.

`langohr.conversion/BytePayload` and `langohr.conversion/to-bytes`
are replaced by `clojurewerkz.support.bytes/ByteSource` and
`clojurewerkz.support.bytes/to-byte-array`, respectively.



## Change Log

[Langohr change log](https://github.com/michaelklishin/langohr/blob/master/ChangeLog.md) is available on GitHub.


## Langohr is a ClojureWerkz Project

[Langohr](http://clojurerabbitmq.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Elastisch](http://clojureelasticsearch.info), a minimalistic well documented Clojure client for ElasticSearch
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client built around CQL 3.0
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Langohr, you may also like [our other
projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
