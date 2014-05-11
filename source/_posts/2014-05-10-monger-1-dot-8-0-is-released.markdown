---
layout: post
title: "Monger 1.8.0 is released"
date: 2014-05-10 20:07:00 -0400
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

`1.8.0` is a minor *backwards-compatible* release that updates MongoDB Java driver
and adds a few minor features. The next release will be `2.0` with some
[major breaking API changes](http://blog.clojurewerkz.org/blog/2014/04/26/major-breaking-public-api-changes-coming-in-our-projects/) that we've announced earlier.


## Changes between 1.7.0 and 1.8.0

### Clojure 1.6

Monger now depends on `org.clojure/clojure` version `1.6.0`. It is
still compatible with Clojure 1.4 and if your `project.clj` depends on
a different version, it will be used, but 1.6 is the default now.

### monger.result Use with WriteConcerns is Deprecated

MongoDB Java driver 2.12.x [no longer guarantees connection affinity](https://github.com/mongodb/mongo-java-driver/releases/tag/r2.12.0-rc0) for thread pool
threads.

This means that `WriteConcern#getLastError` is no longer a safe from concurrency
hazards. Therefore the use of `monger.result` functions on `WriteConcern` instances
is now **deprecated** in MongoDB Java client and Monger.

### MongoDB Java Driver Update

MongoDB Java driver dependency has been [updated to 2.12.x](https://github.com/mongodb/mongo-java-driver/releases/tag/r2.12.0-rc0).

### Default WriteConcern Change

Monger now uses [`WriteConcern/ACKNOWLEDGED`](http://api.mongodb.org/java/2.12/com/mongodb/WriteConcern.html#ACKNOWLEDGED) by default. Functionality-wise
it is the same as `WriteConcern/SAFE` in earlier versions.

### monger.core/connect-via-uri

`monger.core/connect-via-uri` is a version of `monger.core/connect-via-uri!`
which returns the connection instead of mutating a var.

It should be used by projects that are built from reloadable
components, together with `monger.multi.*`.


## Future Plans

The next Monger release will be `2.0` with some [major breaking API
changes](http://blog.clojurewerkz.org/blog/2014/04/26/major-breaking-public-api-changes-coming-in-our-projects/)
that we've announced earlier.



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
