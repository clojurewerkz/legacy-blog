---
layout: post
title: "Neocons 2.0.1 is released"
date: 2013-12-12 21:58
comments: false
categories:
  - neocons
  - releases
---

## TL;DR

Neocons is a feature rich idiomatic [Clojure client for the Neo4J REST API](http://clojureneo4j.info).

`2.0.1` is a bug fix release that focuses on Neo4J 2.0 GA compatibility.



## Changes between Neocons 2.0.0 and 2.0.1

### clj-http upgraded to 0.7.8

Neocons now uses clj-http 0.7.8.


### Neo4J 2.0 Index Creation Fix

Neocons will now use a key name accepted by Neo4J 2.0.0-rc1
when creating indexes.

Contributed by Rohit Aggarwal.




## Change Log

We recommend all users to upgrade to [2.0.1](https://clojars.org/clojurewerkz/neocons/versions/2.0.1) as soon as possible. It will provide full Neo4J 2.0 compatibility.

[Neocons change log](https://github.com/michaelklishin/neocons/blob/2.0.x-stable/ChangeLog.md) is available on GitHub.



## Neocons is a ClojureWerkz Project

[Neocons](http://clojureneo4j.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Monger, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
