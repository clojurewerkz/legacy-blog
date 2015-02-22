---
layout: post
title: "Monger 2.1.0 is released"
date: 2015-02-22 17:47:24 +0300
comments: false
categories:
  - monger
  - mongodb
  - releases
---

## TL;DR

Monger is an idiomatic [Clojure MongoDB driver](http://clojuremongodb.info) for a more civilized age.
It has batteries included, offers powerful expressive query DSL, strives to support every MongoDB 2.0+ feature and has sane defaults.
It also has [solid documentation](http://clojuremongodb.info).

`2.1.0` is a compatibility release. Next feature release of Monger will be `3.0` and will
use [version `3.0` of the MongoDB Java driver](https://github.com/mongodb/mongo-java-driver/releases/tag/r3.0.0-beta2).


## Changes between 2.0.0 and 2.1.0

### Clojure 1.7 Compatibility

Improved Clojure 1.7 (development milestone) releases.

### MongoDB Java Driver Update

MongoDB Java driver dependency has been updated to `2.13.x`.

### $each Operator

The `$each` operator now can be used via `monger.operators`.

Contributed by Juha Jokimäki.



## Change Log

[Monger change log](https://github.com/michaelklishin/monger/blob/master/ChangeLog.md) is available on GitHub.



## Monger is a ClojureWerkz Project

[Monger](http://clojuremongodb.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client built around CQL
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Monger, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


## About the Author

[@michaelklishin](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
