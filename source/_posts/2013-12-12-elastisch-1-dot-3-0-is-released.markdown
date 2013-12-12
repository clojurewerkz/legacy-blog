---
layout: post
title: "Elastisch 1.3.0 is released"
date: 2013-12-12 22:21
comments: false
categories:
  - elastisch
  - elasticsearch
  - releases
---

## TL;DR

Elastisch is a battle tested, small but feature rich and well documented [Clojure client for ElasticSearch](http://clojureelasticsearch.info).
It supports virtually every Elastic Search feature and has [solid documentation](http://clojureelasticsearch.info).

`1.3.0` is a minor feature and usability release. We recommend all users to upgrade to it.

We recommend all users to upgrade to [1.3.0](https://clojars.org/clojurewerkz/elastisch/versions/1.3.0) as soon as possible.


## Changes between Elastisch 1.2.0 and 1.3.0

### :sort Option Can Be a SortBuilder

`:sort` option can now be a `com.elasticsearch.search.sort.SortBuilder` instance
and not just a string.

Contributed by Mark Wong-VanHaren.

### ElasticSearch Native Client Upgrade

Elastisch now depends on ElasticSearch native client version `0.90.7`.

### Bulk Indexing Fix

Elastisch no longer erroneously inserts `_index` and `_type` fields
into documents inserted via bulk API.

Contributed by Max Barnash.

### Result Scrolling as Lazy Sequences

`clojurewerkz.elastisch.native.document/scroll-seq` and
`clojurewerkz.elastisch.rest.document/scroll-seq`
are new functions that accept a search query response
and return a lazy sequence of paginated search results.

This makes working with result sets that require pagination
much more natural:

``` clojure
(require '[clojurewerkz.elastisch.native.document :as doc])

(let [index-name   "articles"
      mapping-type "article"
      res-seq      (doc/scroll-seq
                       (doc/search index-name mapping-type
                                   :query (q/term :title "Emptiness")
                                   :search_type "query_then_fetch"
                                   :scroll "1m"
                                   :size 2))]
    res-seq))
```

Contributed by Max Barnash.


### Upserts in Native Client

Native client now supports upserts of documents:

``` clojure
(require '[clojurewerkz.elastisch.native.document :as doc])

(doc/upsert "people" "person" "elastisch" {:name "Elastisch" :language "Clojure"})
```

### Date Histogram Fix

Date histogram in the native client now includes `:total` field.

Contributed by Jim Dunn.


### Fields in Search Hit Results in Native Client

Native client now returns the same value in `:fields` and `:_fields`
keys in search hits. This makes it both backwards compatible with
earlier versions and the format ElasticSearch HTTP API uses.


### Bulk Index and Delete Operations Support More Options

Bulk index and delete operations support `_parent` and `_routing`
keys.

Contributed by Baptiste Fontaine.

### Clojure 1.3 Support Dropped

Elastisch now requires Clojure 1.4.


### Cheshire Update

[Cheshire](https://github.com/dakrone/cheshire/) dependency has been upgraded to version `5.2.0`.

[Elastisch change log](https://github.com/clojurewerkz/elastisch/blob/1.3.x-stable/ChangeLog.md) is available on GitHub.


## Thank You, Contributors

Kudos to

 * Max Barnash
 * Jim Dunn
 * Baptiste Fontaine
 * Mark Wong-VanHaren

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
