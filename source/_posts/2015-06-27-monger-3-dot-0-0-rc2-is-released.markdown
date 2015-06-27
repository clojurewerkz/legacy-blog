---
layout: post
title: "Monger 3.0.0-rc2 is released"
date: 2015-06-27 23:12:53 +0300
comments: false
categories:
  - monger
  - releases
  - mongodb
---

## TL;DR

Monger is an idiomatic [Clojure MongoDB driver](http://clojuremongodb.info) for a more civilized age.
It has batteries included, offers powerful expressive query DSL, strives to support every MongoDB 2.0+ feature and has sane defaults.
It also has [solid documentation](http://clojuremongodb.info).

`3.0.0` is a major release based on [version `3.0` of the MongoDB Java driver](https://www.mongodb.com/blog/post/introducing-30-java-driver).

Compared to [3.0.0-rc1](/blog/2015/06/15/monger-3-dot-0-0-rc1-is-released/), this release
has a few bug fixes and a breaking API change in `monger.credentials`.


## Changes between 3.0.0-rc1 and 3.0.0-rc2

### Add allow-disk-use and Cursor Options to Aggregates

`monger.collection/aggregate` now supports `:cursor` and `:allow-disk-use` options.

Contributed by Bartek Marcinowski.


### monger.collection/ensure-index No Longer Shadows clojure.core/name

5-arity of `monger.collection/ensure-index` no longer shadows `clojure.core/name`
and fails with an obscure exception.

Contributed by Joshua Karstendick.


### monger.core/connect No Longer Ignores the :uri Option

`monger.core/connect` no longer ignores the `:uri` option. Note that
`monger.core/connect-via-uri` is the recommended way of connecting using URIs.

Contributed by Ivan Samsonov.


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
