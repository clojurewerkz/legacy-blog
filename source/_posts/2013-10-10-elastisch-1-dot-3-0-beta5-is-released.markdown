---
layout: post
title: "Elastisch 1.3.0-beta5 is released"
date: 2013-10-10 22:02
comments: false
categories:
  - releases
  - elastisch
---

## TL;DR

Elastisch is a battle tested, small but feature rich and well documented [Clojure client for ElasticSearch](http://clojureelasticsearch.info).
It supports virtually every Elastic Search feature and has [solid documentation](http://clojureelasticsearch.info).

`1.3.0-beta5` is a development milestone release that is compatible with `1.2.0`
and includes one minor feature.


## Changes between Elastisch 1.3.0-beta4 and 1.3.0-beta5

### Upserts in Native Client

Native client now supports upserts of documents:

``` clojure
(require '[clojurewerkz.elastisch.native.document :as doc])

(doc/upsert "people" "person" "elastisch" {:name "Elastisch" :language "Clojure"})
```


## Change log

[Elastisch change log](https://github.com/clojurewerkz/elastisch/blob/master/ChangeLog.md) is available on GitHub.


## Thank You, Contributors

Kudos to Max Barnash for contributing to this release.


## Elastisch is a ClojureWerkz Project

[Elastisch](http://clojureelasticsearch.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client
 * [Titanium](http://titanium.clojurewerkz.org), a Clojure graph library
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Meltdown](http://github.com/clojurewerkz/eep), a Clojure interface to Reactor
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Elastisch, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
