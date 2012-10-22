---
layout: post
title: "Elastisch 1.0.2 is released"
date: 2012-10-22 12:13
comments: true
categories:
  - releases
  - elastisch
---

## TL;DR

Elastisch is a battle tested, small but feature rich and well documented [Clojure client for ElasticSearch](http://clojureelasticsearch.info).
It supports virtually every Elastic Search feature and has [solid documentation](http://clojureelasticsearch.info).

`1.0.2` is a bug fix release. We recommend all users to upgrade to it.


## Changes in 1.0.2

 * Count API now uses GET for requests without the query part ([GH issue #5](https://github.com/clojurewerkz/elastisch/issues/5))
 * Count API No Longer Ignores Mapping Types  ([GH issue #6](https://github.com/clojurewerkz/elastisch/issues/6))

We recommend all users to upgrade to [1.0.2](https://clojars.org/clojurewerkz/elastisch/versions/1.0.2) as soon as possible.

[Elastisch change log](https://github.com/clojurewerkz/elastisch/blob/1.0.x-stable/ChangeLog.md) is available on GitHub.


## Thank You, Contributors

Kudos to Vesa Marttila for reporting both issues fixed in this release.


## Elastisch is a ClojureWerkz Project

[Elastisch](http://clojureelasticsearch.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Welle](https://clojureriak.info), a Riak client with batteries included
 * [Monger](https://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](https://clojureneo4j.info), a client for the Neo4J REST API
 * [Langohr](https://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Quartzite](https://clojurequartz.info), a powerful scheduling library

and several others. If you like Elastisch, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


The [ClojureWerkz](http://clojurewerkz.org) Team
