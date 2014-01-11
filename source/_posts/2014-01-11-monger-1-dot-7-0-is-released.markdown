---
layout: post
title: "Monger 1.7.0 is released"
date: 2014-01-11 20:18
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

`1.7.0` is a minor *backwards-compatible* release that updates MongoDB Java driver
and makes two dependencies optional.


## Changes between 1.6.0 and 1.7.0

### MongoDB Java Driver Update

MongoDB Java driver dependency has been [updated to 2.11.3](https://github.com/mongodb/mongo-java-driver/releases/tag/r2.11.3).

### Ragtime Dependency Dropped

Ragtime is now an optional dependency: if your project uses `monger.ragtime`, you
need to add Ragtime to your own `project.clj`:

``` clojure
[ragtime/ragtime.core          "0.3.4"]
```

### Validateur Dependency Dropped

[Validateur](http://clojurevalidations.info) is no longer a dependency.



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
