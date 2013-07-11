---
layout: post
title: "Elastisch 1.2.0-beta3 is released"
date: 2013-07-11 23:08
comments: false
categories:
  - elastisch
  - releases
---

## TL;DR

Elastisch is a battle tested, small but feature rich and well documented [Clojure client for ElasticSearch](http://clojureelasticsearch.info).
It supports virtually every Elastic Search feature and has [solid documentation](http://clojureelasticsearch.info).

[1.2.0-beta3](https://clojars.org/clojurewerkz/elastisch/versions/1.2.0-beta3) is a development release that
adds `:ignore_indices` parameter support to the REST client.



## Changes between Elastisch 1.2.0-beta1 and 1.2.0-beta3

### ElasticSearch Native Client Upgrade

Elastisch now depends on ElasticSearch native client version `0.90.2`.

### Support for :ignore_indices in REST API client

`clojurewerkz.elastisch.rest.document/search`,
`clojurewerkz.elastisch.rest.document/search-all-types`,
`clojurewerkz.elastisch.rest.document/count`,
`clojurewerkz.elastisch.rest.document/delete-by-query`, and
`clojurewerkz.elastisch.rest.document/delete-by-query-across-all-types`
now accepts the `:ignore_indices` option:

``` clojure
(doc/search [index-name, missing-index-name,...] mapping-type :query (q/match-all)
                                                              :ignore_indices "missing")
```

See also [elasticsearch/guide/reference/api](http://www.elasticsearch.org/guide/reference/api/)

Contributed by Joachim De Beule


## Changes between Elastisch 1.2.0-beta1 and 1.2.0-beta2

### Search Queries with a Subset of Fields are Converted Correctly

Search queries that only retrieve a subset of fields using
the `:fields` option are now correctly converted to Clojure maps.

Contributed by Soren Macbeth.

### ElasticSearch Native Client Upgrade

Elastisch now depends on ElasticSearch native client version `0.90.1`.





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
