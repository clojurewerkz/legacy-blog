---
layout: post
title: "Monger 1.4.0 is released"
date: 2012-11-27 23:39
comments: false
categories: 
  - releases
  - monger
---

## TL;DR

Monger is an idiomatic [Clojure MongoDB driver](http://clojuremongodb.info) for a more civilized age.
It has batteries included, offers powerful expressive query DSL, strives to support every MongoDB 2.0+ feature and has sane defaults.
It also has [solid documentation](http://clojuremongodb.info).

`1.4.0` is a minor *almost (but not completely) backwards-compatible* release that upgrades MongoDB Java driver and
Cheshire and adapts to their public API changes.


## Changes in 1.4.0

### MongoDB Java Driver Update

MongoDB Java driver dependency has been [updated to 2.10.0](https://groups.google.com/forum/?fromgroups#!topic/mongodb-announce/FHp6ue36WUw). If your code depends on the exact
class `com.mongodb.Mongo`, it should be updated to use `com.mongodb.MongoClient` (or not depend on specific class names at all).

In addition, `MongoOptions` and `MongoURI` in the new driver have changed to `MongoClientOptions` and `MongoClientURI`, respectively.


### Cheshire 0.5.0

`monger.json` and `monger.joda-time` will use [Cheshire](https://github.com/dakrone/cheshire) if it is available and now
*requires Cheshire version 5.0*.
[clojure.data.json](https://github.com/clojure/data.json) is no longer a hard dependency (but `0.1.x` versions are still supported if available).

Recently released `clojure.data.json` version `0.2.0` is now supported. We strongly recommend all users to use Cheshire when possible.

[Cheshire 5.0 change log](https://github.com/dakrone/cheshire/blob/master/ChangeLog.md) is available on GitHub.


### ClojureWerkz Support 0.9.0

ClojureWerkz Support library is upgraded to `0.9`.


## Change Log

We recommend all users to upgrade to [1.4.0](https://clojars.org/com.novemberain/monger/versions/1.4.0) as soon as possible.

[Monger change log](https://github.com/michaelklishin/monger/blob/master/ChangeLog.md) is available on GitHub.



## Monger is a ClojureWerkz Project

[Monger](http://clojuremongodb.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Monger, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[@michaelklishin](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
