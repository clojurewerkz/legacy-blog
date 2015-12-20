---
layout: post
title: "Elastisch 2.2.0-rc1 is released"
date: 2015-12-20 18:35:28 +0300
comments: false
categories:
  - elastisch
  - releases
---

## TL;DR

Elastisch is a battle tested, small but feature rich and well
documented [Clojure client for ElasticSearch](http://clojureelasticsearch.info). It supports
virtually every Elastic Search feature and has [solid documentation](http://clojureelasticsearch.info).

[2.2.0-rc1](https://clojars.org/clojurewerkz/elastisch/versions/2.2.0-rc1) is a release
candidate of Elastisch 2.2 which introduces new features and bug fixes.

Elastisch `2.2.0` will be the last release to target ElasticSearch `1.7`. After
that Elastisch development will focus on ElasticSearch `2.x`.


## Changes between Elastisch 2.1.x and 2.2.0-rc1

### Corrected Filter Option Name in Native Client

Native client now uses `:filter` for filters, just like the REST one.

### Add completion and fuzzy suggestors for Native Client

`clojurewerkz.elastisch.native.document` has new function `suggest`
for term autocompletion. It allows filter results by category and
geolocation:

``` clojure
(require '[clojurewerkz.elastisch.native.document :as doc])

(doc/suggest conn index-name :completion "e" {:context {:gender "female"}})
(doc/suggest conn index-name :fuzzy "esmor" {:fuzziness 1 :min-length 2})
```

Contributed by Timo Sulg (@timgluz).

### Fixed `index/close` and `index/open` argument type error

  `clojurewerkz.elastisch.native.conversion/->open-index-request` and  `->close-index-request`
  passed plain string to [CloseIndexRequest](http://javadoc.kyubu.de/elasticsearch/HEAD/org/elasticsearch/action/admin/indices/close/CloseIndexRequest.html) constructor, but it expected values passed as array of string.
  Fixed it with existing function `conversion/->string-array` and added missing tests for this usecase
  into `clojurewerkz.elastisch.native-api.indices-settings-test`.

  Contributed by Timo Sulg (@timgluz).

### Fixed `update-with-script` in Native Client

`clojurewerkz.elastisch.native.conversion/->update-request` arguments
updated in `clojurewerkz.elastisch.native.document/update-with-script` to reflect
recent changes.

Contributed by Michael Nussbaum.

### Index Stats Update

`clojurewerkz.elastisch.rest.index/stats` has been updated for ElasticSearch `1.3.x`
and later versions.

Contributed by Roman Pearah.

### `create` Bulk Operation Helper

Bulk operation helper functions now include `create`.

Contributed by @nikopol.

### allow setting `:ignore-unmapped` in query sort instructions

In both native and rest apis, `:ignore-unmapped` may be set in the query by specifying
a sort field-name and option-map instead of order name with the `query/sort` function.
For example:


``` clojure
(require '[clojurewerkz.elastisch.native.document :as doc])
(require '[clojurewerkz.elastisch.query :as q])

(doc/search conn index type
            {:query (q/query-string :query "software" :default_field "summary")
             :sort  (q/sort "unmapped-field-name" {:ignore_unmapped true
                                                   :order "asc"})})
```

Contributed by @ryfow

### allow setting `:ignore_unmapped` in query sort instructions

In both native and rest apis, `:ignore-unmapped` may be set in the query by specifying
a sort field-name and option-map instead of order name with the `query/sort` function.
For example:


``` clojure
(require '[clojurewerkz.elastisch.native.document :as doc])
(require '[clojurewerkz.elastisch.query :as q])

(doc/search conn [index-name missing-index-name] 
                                             mapping-type
                                             :query   (q/match-all)
                                             :ignore_unavailable true)
```

Contributed by Joachim De Beule.

### `scan-and-scroll-seq` helper

`scan-and-scroll-seq` provides an easier-to-use abstraction over ES's
scan and scroll API, wrapping `scroll-seq` and handling the
special-case first request.

Contributed by @loganmhb

### ElasticSearch Java Client Upgrade

Elastisch now depends on ElasticSearch Java client version `1.7.x`.

### clj-http Update

[clj-http](https://github.com/dakrone/clj-http/) dependency has been upgraded to version `2.0.x`.

### Better support for plural/single indices and aliases in native update-aliases

* `:remove` action now works with singular `:index` key 
* multiple aliases can be added with single `:add` action
* alias can be removed from multiple indices with single `:remove` action

Contributed by @mnylen

### Index Settings Now Allow Keywordized Keys When Creating Index Using Native API

Previously only mappings allowed keys to be keywords, now same works with index settings.

Contributed by @mnylen

### Support for Large Scroll IDs

Elastisch now supports scroll IDs larger than 4 KB.


Contributed by niko.


### Bulk Operation Support in Native Client

Native client now supports bulk operations with the same API as the REST one.

Contributed by

 * Mitchel Kuijpers (Avisi)
 * Michael Nussbaum and Jack Lund (Braintree)


### Fixed unregister-query in Native Client

`clojurewerkz.elastisch.native.percolation/unregister-query` arguments
were mistakenly swapped when delegating to the Java client.

Contributed by Stephen Muss.

### Guava Excluded From Dependencies

Contributed by Jan Stępień (Stylefruits).

## Add support for Nested Aggregations in the Native Client

Native client now supports nesting in the following aggregations

 * `histogram`
 * `date_histogram`
 * `range`
 * `date_range`
 * `terms`

Contributed by Mitchel Kuijpers (Avisi).

### ElasticSearch Java Client Upgrade

Elastisch now depends on ElasticSearch Java client version `1.4.x`.

### clj-http Update

[clj-http](https://github.com/dakrone/clj-http/) dependency has been upgraded to version `1.0.1`.

### Cheshire Update

[Cheshire](https://github.com/dakrone/cheshire/) dependency has been upgraded to version `5.4.0`.




## Full Change Log

[Elastisch change log](https://github.com/clojurewerkz/elastisch/blob/master/ChangeLog.md) is available on GitHub.


## Thank You, Contributors

Kudos to Michael Nussbaum and Jeffrey Erikson for contributing to this release.


## Elastisch is a ClojureWerkz Project

[Elastisch](http://clojureelasticsearch.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Elastisch, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
