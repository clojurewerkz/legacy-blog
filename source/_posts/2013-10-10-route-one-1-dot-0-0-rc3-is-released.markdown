---
layout: post
title: "Route One 1.0.0-rc3 is released"
date: 2013-10-10 22:19
comments: false
categories:
  - releases
  - route-one
---

[Route One](https://github.com/clojurewerkz/route-one) is a Clojure DSL for URL/URI/path generation
from a route map, compatible with Compojure's [Clout](https://github.com/weavejester/clout).

`1.0.0-rc3` is a release candidate that introduces one small Compojure
integration feature.


## Changes Between 1.0.0-rc2 and 1.0.0-rc3

### Catch All Route

`clojurewerkz.route-one.compojure/catch-all` is a new helper macro that
generates a route that matches any path.

It is useful for defining fallback routes (such as 404 or 500 status pages).



## Change log

[Route One change log](https://github.com/clojurewerkz/route-one/blob/master/ChangeLog.md) is available on GitHub.


## Route One is a ClojureWerkz Project

Route One is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a small feature complete Clojure client for ElasticSearch
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Titanium](http://titanium.clojurewerkz.org), a Clojure graph library
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Elastisch, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
