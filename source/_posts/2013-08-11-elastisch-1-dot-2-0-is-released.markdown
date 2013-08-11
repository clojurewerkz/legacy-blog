---
layout: post
title: "Elastisch 1.2.0 is released"
date: 2013-08-11 22:49
comments: false
categories:
  - elastisch
  - releases
---

## TL;DR

Elastisch is a battle tested, small but feature rich and well documented [Clojure client for ElasticSearch](http://clojureelasticsearch.info).
It supports virtually every Elastic Search feature and has [solid documentation](http://clojureelasticsearch.info).

`1.2.0` is a minor feature and usability release. We recommend all users to upgrade to it.


## Changes in Elastisch 1.2.0

### ElasticSearch Native Client Upgrade

Elastisch now depends on ElasticSearch native client version `0.90.3`.


### Empty Bulk Operations are Ignored

Elastisch now will not perform a bulk operation if its list of operations is empty.

Contributed by Baptiste Fontaine.


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

### Search Queries with a Subset of Fields are Converted Correctly

Search queries that only retrieve a subset of fields using
the `:fields` option are now correctly converted to Clojure maps.

Contributed by Soren Macbeth.

### ElasticSearch Native Client Upgrade

Elastisch now depends on ElasticSearch native client version `0.90.1`.


### Sort Improvements for Search Queries

`clojurewerkz.elastisch.native.document/search` now accepts maps as
`:search` option values:

``` clojure
(doc/search index-name mapping-type :query (q/match-all)
                                    :sort  (array-map "title" "asc")
```

This is identical to how the option works with the REST client.


We recommend all users to upgrade to [1.2.0](https://clojars.org/clojurewerkz/elastisch/versions/1.2.0) as soon as possible.


## Change log

[Elastisch change log](https://github.com/clojurewerkz/elastisch/blob/1.2.x-stable/ChangeLog.md) is available on GitHub.


## Thank You, Contributors

Kudos to

 * Joachim De Beule
 * Baptiste Fontaine
 * Soren Macbeth

for contributing to this release.


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


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
