---
layout: post
title: "Langohr 1.1.0 is released"
date: 2013-07-31 10:31
comments: false
categories:
  - langohr
  - releases
---

## TL;DR

Langohr is a [Clojure RabbitMQ client](http://clojurerabbitmq.info) that embraces [AMQP 0.9.1 Model](http://www.rabbitmq.com/tutorials/amqp-concepts.html).

`1.1.0` is a minor feature release that primarily introduces HTTP API improvements.


## Changes between Langohr 1.0.1 and 1.1.0

### Extended HTTP API Support

`langohr.http` now provides more complete coverage of the RabbitMQ HTTP API.

Contributed by Steffen Dienst.

### langohr.consumers/subscribe Options In Line with Docs

The documentation says to use function handler keys ending in
"-fn", but this code currently only recognizes the old form. This
commit ensures that all keys that are used within
`langohr.consumers/subscribe` can be used as a parameter.

Contributed by Steffen Dienst.

### langohr.core/connect-to-first-available is Removed

`langohr.core/connect-to-first-available` is removed. A better failover functionality
will be available in future versions.

### RabbitMQ Java Client Upgrade

RabbitMQ Java client dependency has been updated to `3.1.3`.

### clj-http Upgrade

clj-http dependency has been updated to `0.7.4`.

### Cheshire Upgrade

Cheshire dependency has been updated to `5.2.0`.



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
