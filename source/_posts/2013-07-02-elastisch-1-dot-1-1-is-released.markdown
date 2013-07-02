---
layout: post
title: "Elastisch 1.1.1 is released"
date: 2013-07-02 22:14
comments: false
categories:
  - elastisch
  - releases
---

## TL;DR

Elastisch is a battle tested, small but feature rich and well documented [Clojure client for ElasticSearch](http://clojureelasticsearch.info).
It supports virtually every Elastic Search feature and has [solid documentation](http://clojureelasticsearch.info).

`1.1.1` is a bug fix release. We recommend all users to upgrade to it.


## Changes in 1.1.1

### Search Queries with a Subset of Fields are Converted Correctly

Search queries that only retrieve a subset of fields using
the `:fields` option are now correctly converted to Clojure maps.

Contributed by Soren Macbeth.


We recommend all users to upgrade to [1.1.1](https://clojars.org/clojurewerkz/elastisch/versions/1.1.1) as soon as possible.

[Elastisch change log](https://github.com/clojurewerkz/elastisch/blob/1.0.x-stable/ChangeLog.md) is available on GitHub.


## Thank You, Contributors

Kudos to Soren Macbeth for contributing a fix to this release.


## Elastisch is a ClojureWerkz Project

[Elastisch](http://clojureelasticsearch.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client
 * [Titanium](http://titanium.clojurewerkz.org), a Clojure graph library
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Elastisch, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
