---
layout: post
title: "Elastisch 2.0.0-rc2 is released"
date: 2014-06-08 22:35:18 +0400
comments: false
categories:
  - elastisch
  - releases
---

## TL;DR

Elastisch is a battle tested, small but feature rich and well
documented [Clojure client for ElasticSearch](http://clojureelasticsearch.info). It supports
virtually every Elastic Search feature and has [solid
documentation](http://clojureelasticsearch.info).

[2.0.0-rc2](https://clojars.org/clojurewerkz/elastisch/versions/2.0.0-rc2)
is a release candidate of Elastisch 2.0, which focuses on the new
features in ElasticSearch 1.1 and introduces major API improvements,
including a **breaking change**.


## Changes between Elastisch 2.0.0-rc1 and 2.0.0-rc2

### ElasticSearch Client Update

ElasticSearch client has been upgraded to `1.2.x`.

### Snapshotting Support in Native Client

Native client now supports snapshotting (updated for ElasticSearch 1.2)
with the same Clojure API as the REST client (all the usual API conventions
apply).



## Full Change Log

[Elastisch change log](https://github.com/clojurewerkz/elastisch/blob/master/ChangeLog.md) is available on GitHub.


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


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
