---
layout: post
title: "Elastisch 1.2.0-beta1 is released"
date: 2013-06-15 12:30
comments: true
categories:
  - elastisch
  - releases
---

## TL;DR

Elastisch is a battle tested, small but feature rich and well documented [Clojure client for ElasticSearch](http://clojureelasticsearch.info).
It supports virtually every Elastic Search feature and has [solid documentation](http://clojureelasticsearch.info).

[1.2.0-beta1](https://clojars.org/clojurewerkz/elastisch/versions/1.2.0-beta1) is a development release that has improved sorting support in the native client.



## Changes between Elastisch 1.1.0 and 1.2.0-beta1

### Sort Improvements for Search Queries

`clojurewerkz.elastisch.native.document/search` now accepts maps as
`:search` option values:

``` clojure
(doc/search index-name mapping-type :query (q/match-all)
                                    :sort  (array-map "title" "asc")
```

This is identical to how the option works with the REST client.




## Elastisch is a ClojureWerkz Project

[Elastisch](http://clojureelasticsearch.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Cassaforte](http://clojurecassandra.info), an easy to use Clojure Cassandra client built around CQL3
 * [Titanium](http://titanium.clojurewerkz.org), a powerful graph library on top of the [Tinkerpop stack](http://tinkerpop.com)
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Elastisch, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
