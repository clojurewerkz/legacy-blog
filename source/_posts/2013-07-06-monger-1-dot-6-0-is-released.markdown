---
layout: post
title: "Monger 1.6.0 is released"
date: 2013-07-06 23:35
comments: false
categories:
  - monger
  - releases
---

## TL;DR

Monger is an idiomatic [Clojure MongoDB driver](http://clojuremongodb.info) for a more civilized age.
It has batteries included, offers powerful expressive query DSL, strives to support every MongoDB 2.0+ feature and has sane defaults.
It also has [solid documentation](http://clojuremongodb.info).

`1.6.0` is a minor *completely backwards-compatible* release that makes it easier to use
Monger with multiple databases and MongoDB servers.


## Changes between 1.5.0 and 1.6.0

### monger.multi.collection

`monger.multi.collection` is a new namespace with functions that are very similar to those
in the `monger.collection` namespace but always take a database reference as an explicit argument.

They are supposed to be used in cases when relying on `monger.core/*mongodb-database*` is not
enough.

Erik Bakstad contributed most of this work.


### MongoDB Java Driver Update

MongoDB Java driver dependency has been [updated to 2.11.2](https://github.com/mongodb/mongo-java-driver/wiki/Release-Notes).


### monger.core/drop-db

`monger.core/drop-db` is a new function that drops a database by name.


### One More Cache Implementation

`monger.cache/db-aware-monger-cache-factory` will return a MongoDB-backed `clojure.core.cache`
implementation that can use any database:

``` clojure
(require '[monger.core  :as mg])
(require '[monger.cache :as cache])

(let [db   (mg/get-db "altcache")
      coll "cache_entries"
      c    (cache/db-aware-monger-cache-factory db coll)]
  (comment "This cache instance will use the altcache DB"))
```

### Ragtime changes

Bug fix: `monger.ragtime/applied-migration-ids` now returns a vector (instead of a set) in order to preserve the original creation order of the migrations.

Ragtime dependency has been updated to 0.3.3.


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


[@michaelklishin](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
