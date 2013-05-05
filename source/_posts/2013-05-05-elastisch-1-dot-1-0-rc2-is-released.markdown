---
layout: post
title: "Elastisch 1.1.0-rc2 is released"
date: 2013-05-05 14:02
comments: false
categories:
  - elastisch
  - releases
---

## TL;DR

Elastisch is a battle tested, small but feature rich and well documented [Clojure client for ElasticSearch](http://clojureelasticsearch.info).
It supports virtually every Elastic Search feature, provides both HTTP and native clients
(as of `1.1`) and has [solid documentation](http://clojureelasticsearch.info).

`1.1.0-rc2` is a preview release that improves native client performance.


## Changes in 1.1.0-rc2

### Native Client Performance Improvements

Native client is now over 50% faster on most commonly used operations
thanks to much lower conversion overhead from ElasticSearch native client
data structures to Clojure maps.

[Elastisch change log](https://github.com/clojurewerkz/elastisch/blob/master/ChangeLog.md) is available on GitHub.


## Thank You, Contributors

Kudos to Jon Pither and Antonio Terreno for doing the benchmarking,
profiling and optimizations that made this substantial performance
increase a reality.


## Elastisch is a ClojureWerkz Project

[Elastisch](http://clojureelasticsearch.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Titanium](http://titanium.clojurewerkz.org), a powerful Clojure graph library
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Elastisch, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
