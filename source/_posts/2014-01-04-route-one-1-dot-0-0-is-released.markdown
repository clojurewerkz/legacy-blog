---
layout: post
title: "Route One 1.0.0 is released"
date: 2014-01-04 17:06
comments: false
categories:
  - route-one
  - releases
---

[Route One](https://github.com/clojurewerkz/route-one) is a Clojure DSL for URL/URI/path generation
from a route map, compatible with Compojure's [Clout](https://github.com/weavejester/clout).

`1.0.0` fixes one compatibility issue with Compojure integration.


## Changes Between 1.0.0-rc3 and 1.0.0

### url-for Preserves Paths From Base URL

Leading path component from `*base-url*` is now preserved when
constructing path in `url-for`.

Contributed by Ray Miller.



## Change log

[Route One change log](https://github.com/clojurewerkz/route-one/blob/master/ChangeLog.md) is available on GitHub.


## Route One is a ClojureWerkz Project

Route One is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a small feature complete Clojure client for ElasticSearch
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Titanium](http://titanium.clojurewerkz.org), a Clojure graph library
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Elastisch, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).

## About The Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
