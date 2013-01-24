---
layout: post
title: "Neocons 1.0.3 is released"
date: 2013-01-24 14:15
comments: false
categories:
  - releases
  - neocons
---

## TL;DR

Neocons is a feature rich idiomatic [Clojure client for the Neo4J REST API](http://clojureneo4j.info).

`1.0.3` is a *100% backwards-compatible* bug fix release.



## Changes between Neocons 1.0.2 and 1.0.3

### clojurewerkz.neocons.rest.relationship/maybe-create Now Fully Supports Ids

`clojurewerkz.neocons.rest.relationship/maybe-create` now correctly works with node ids
as well as `Node` records.

GH issue: #19.




## Change Log

We recommend all users to upgrade to [1.0.3](https://clojars.org/clojurewerkz/neocons/versions/1.0.3) as soon as possible.

[Neocons change log](https://github.com/michaelklishin/neocons/blob/1.0.x-stable/ChangeLog.md) is available on GitHub.



## Neocons is a ClojureWerkz Project

[Neocons](http://clojureneo4j.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](https://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](https://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Monger](https://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Welle](https://clojureriak.info), a Riak client with batteries included
 * [Quartzite](https://clojurequartz.info), a powerful scheduling library

and several others. If you like Monger, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
