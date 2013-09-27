---
layout: post
title: "Elastisch 1.3.0-beta3 is released"
date: 2013-09-27 08:50
comments: false
categories:
  - elastisch
  - releases
---

## TL;DR

Elastisch is a battle tested, small but feature rich and well documented [Clojure client for ElasticSearch](http://clojureelasticsearch.info).
It supports virtually every Elastic Search feature and has [solid documentation](http://clojureelasticsearch.info).

`1.3.0-beta3` is a development milestone release that is compatible with `1.2.0`
and comes with one usability improvement and updated ElasticSearch Java client.


## Changes between Elastisch 1.3.0-beta2 and 1.3.0-beta3

### Fields in Search Hit Results in Native Client

Native client now returns the same value in `:fields` and `:_fields`
keys in search hits. This makes it both backwards compatible with
earlier versions and the format ElasticSearch HTTP API uses.


### ElasticSearch Native Client Upgrade

Elastisch now depends on ElasticSearch native client version `0.90.5`.


## Change log

[Elastisch change log](https://github.com/clojurewerkz/elastisch/blob/master/ChangeLog.md) is available on GitHub.


## Thank You, Contributors

Kudos to konradkonrad for contributing to this release.


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
