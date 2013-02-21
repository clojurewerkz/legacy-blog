---
layout: post
title: "Monger 1.5.0-beta1 is released"
date: 2013-02-21 22:37
comments: false
categories: 
  - releases
  - monger
---

## TL;DR

Monger is an idiomatic [Clojure MongoDB driver](http://clojuremongodb.info) for a more civilized age.
It has batteries included, offers powerful expressive query DSL, strives to support every MongoDB 2.0+ feature and has sane defaults.
It also has [solid documentation](http://clojuremongodb.info).

`1.5.0` is a minor *completely backwards-compatible* release that includes updated
dependencies and very minor improvements.


## Changes in 1.5.0-beta1

### Explicit DBCursor Closure by monger.collection/find-maps and the like

`monger.collection/find-maps` and the like will now explicitly close DB cursors.

GH issue: #47

### MongoDB Java Driver Update

MongoDB Java driver dependency has been [updated to 2.10.1](https://groups.google.com/forum/?fromgroups=#!topic/mongodb-announce/y3UQDTVeduA).


### Cheshire 5.0.2

[Cheshire](https://github.com/dakrone/cheshire), the Clojure JSON serialization library used by
`monger.json` and `monger.joda-time` extensions, has been upgraded to `5.0.2`.

[Cheshire 5.0 change log](https://github.com/dakrone/cheshire/blob/master/ChangeLog.md) is available on GitHub.


### ClojureWerkz Support 0.14.0

ClojureWerkz Support library is upgraded to `0.14`.


## Change Log

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
