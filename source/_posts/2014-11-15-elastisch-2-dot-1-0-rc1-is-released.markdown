---
layout: post
title: "Elastisch 2.1.0-rc1 is released"
date: 2014-11-15 01:50:10 +0300
comments: false
categories:
  - elastisch
  - releases
---

## TL;DR

Elastisch is a battle tested, small but feature rich and well
documented [Clojure client for ElasticSearch](http://clojureelasticsearch.info). It supports
virtually every Elastic Search feature and has [solid documentation](http://clojureelasticsearch.info).

[2.1.0-rc1](https://clojars.org/clojurewerkz/elastisch/versions/2.1.0-rc1) is a release
candidate of Elastisch 2.1, coming to you after 9 beta releases.

## Changes between Elastisch 2.1.0-beta9 and 2.1.0-rc1

### ElasticSearch Native Client Upgrade

Elastisch now depends on ElasticSearch native client version `1.4.x`.

### Clojure 1.4 Support Dropped

Elastisch no longer officially supports Clojure 1.4. Most of the functionality
still works well on that version but please don't file bugs specific to that
version.


### Allow `:index` key in `update-aliases` (native)

`clojurewerkz.elastisch.native.index/update-aliases` expects indices to be added to be specified in the
`:indices` key while the respective REST function uses `:index`. This can have unexpected results, namely
the creation of the respective alias for _all_ indices. It is now possible to supply either `:index` or
`:indices` to the function.

GH issue: [#108](https://github.com/clojurewerkz/elastisch/issues/108).

Contributed by Yannick Scherer (stylefruits)

### Update with Partial Document via native API

`clojurewerkz.elastisch.native.document/update-with-partial-doc` is a new function
in the Native Client (existed before in the REST API) that performs
[partial updates](http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/partial-updates.html):

``` clojure
(require '[clojurewerkz.elastisch.native.document :as doc])

(doc/update-with-partial-doc conn "people" "person" "1" {:country "Sweden"})
```

Note that the REST API should now be called without wrapping the document in a `:doc` key.
I.e. change `{:doc {:field-to-update "Update"}}` to `{:field-to-update "Update"}`.

Contributed by Henrik Lundahl.


## Changes between Elastisch 2.0.0 and 2.1.0-beta9

### Ability to Specify Aliases In index.create-template

`clojurewerkz.elastisch.rest.index.create-template` now supports
the `:aliases` option:

``` clojure
(require '[clojurewerkz.elastisch.rest.index :as idx])

(idx/create-template conn "accounts" {:template "account*" :settings {:index {:refresh_interval "60s"}} :aliases {:account-alias {}}})
```

Contributed by Jeffrey Erikson.


### clj-http Update

[clj-http](https://github.com/dakrone/clj-http/) dependency has been upgraded to version `1.0.x`.

### Allow Retry On Conflict Option

Updates and upserts now allow the `retry-on-conflict` option to be set.
This helps to work around Elasticsearch version conflicts.

GH issue: [#119](https://github.com/clojurewerkz/elastisch/issues/119).

Contributed by Michael Nussbaum (Braintree).


### REST API Bulk Indexing Filters Out Operation Keys

`clojurewerkz.elastisch.rest.bulk/bulk-index` now filters out
all operation/option keys so that they don't get stored in the document
body.

GH issue: [#116](https://github.com/clojurewerkz/elastisch/issues/116).

Contributed by Michael Nussbaum (Braintree).


### New Line in Multi-Search REST API

ElasticSearch Multi Search REST API endpoint is sensitive to the trailing new line.
When it is missing, the response contains one result too few.

Elastisch now makes sure to append a new line to Multi Search request
bodies.

### Correct async-put in Native Client

Native client's `document/async-put` no longer fails with an exception.

Contributed by Nikita Burtsev.

### clj-time 0.8.0

[clj-time](https://github.com/clj-time/clj-time) dependency has been upgraded to version 0.8.0.


### ElasticSearch Native Client Upgrade

Elastisch now depends on ElasticSearch native client version `1.3.x`.

### Single-Bucket Aggregation Fix in the Native Client

Child aggregations in single-bucket aggregations (i.e. "global") are no longer silently dropped.

Contributed by Yannick Scherer (StyleFruits).


### Aggregations Support in the Native Client

Native client now has support for [aggregations](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/search-aggregations.html).

The API is [the same as in the REST client](http://clojureelasticsearch.info/articles/aggregation.html).

Note that ElasticSearch 1.2 has 26 aggregations. Currently only the most commonly
used ones are supported but support for more types will be added eventually.
The supported types are:

 * Avg
 * Max
 * Min
 * Sum
 * Stats
 * Extended stats
 * Cardinality, value count
 * Percentiles
 * Histogram
 * Date Histogram
 * Range
 * Date Range
 * Terms
 * Missing
 * Global

### Multi-Search Support in the Native Client

Native client now has support for [multi-search](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/search-multi-search.html).

The API is [the same as in the REST client](http://clojureelasticsearch.info/articles/querying.html#performing-queries) except that the functions are in the
`clojurewerkz.elastisch.native.multi`.

### Extra Options on Upserts

`clojurewerkz.elastisch.native.document/upsert` now accepts a map of extra options,
e.g. parent document ID:

``` clojure
(doc/upsert conn index-name index-type id doc {:parent parent-id})
```

### Terms Query Helper

`clojurewerkz.elastisch.query/terms` is a newly added alias for `clojurewerkz.elastisch.query/term`
when used with a collection.

Contributed by Martin Klepsch.

### Remove Alias Now Works in Native Client

Bug fixed in native client for removing aliases from indices and
improved inline documentation. [See aliases in the guide](http://clojureelasticsearch.info/articles/indexing.html#index-aliases).

GH issue: [#98](https://github.com/clojurewerkz/elastisch/issues/98).


### Highlighting Support in Native Client

Native client now supports (most of the) [highlighting features](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/search-request-highlighting.html)
the REST client does:

``` clojure
(require '[clojurewerkz.elastisch.native.document :as doc])
(require '[clojurewerkz.elastisch.query :as q])

(doc/search conn index type
            {:query (q/query-string :query "software" :default_field "summary")
             :highlight {:fields {:summary {}}}})
```


### Per Connection clj-http Options in REST Client

It is now possible to specify clj-http options for REST API connections,
e.g. to specify a timeout:

``` clojure
(esr/connect "http://127.0.0.1:9200/" {:conn-timeout 1000
                                       :basic-auth ["username" "pa$$w0rd"]})
```

### Source Filtering Support in Native Client

Native client now supports [source filtering](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/search-request-source-filtering.html)
just like the REST API client:

``` clojure
(doc/search conn index-name mapping-type
            :query   (q/match-all)
            :sort    {"first-name" "asc"}
            :_source ["first-name" "age"])
```

``` clojure
(doc/search conn index-name mapping-type
            :query   (q/match-all)
            :sort    {"first-name" "asc"}
            :_source {"exclude" ["title" "country"
                                 "planet" "biography"
                                 "last-name" "username"]})
```

GH issue: [#73](https://github.com/clojurewerkz/elastisch/issues/73).

### Search Can Return Fields and Source

Previously a search would return either the source document, or specific fields and not
both.  There are certain circumstances where having both are beneficial, for example when
searching for a child document and you want to include the parent ID:

```clojure
(require '[clojurewerkz.elastisch.native.document :as esd])

(esd/search conn "index" "child-type" :query (q/match-all) :fields ["_parent"])
```

The above would return the parent document ID in the ```:_parent``` field of each hit, but
would not return the document itself.  You can now have both by:

```clojure
(esd/search conn "index" "child-type" :query (q/match-all) :fields ["_parent" "_source"])
```

Now the parent ID is in the ```:_parent``` field of each hit, and the matching document
will be in ```:_source``` as per a normal search.

Contributed by Ben Ashford.


### Update with Partial Document

`clojurewerkz.elastisch.rest.document/update-with-partial-doc` is a new function
that performs [partial updates](http://www.elasticsearch.org/guide/en/elasticsearch/guide/current/partial-updates.html):

``` clojure
(require '[clojurewerkz.elastisch.rest.document :as doc])

(doc/update-with-partial-doc conn "people" "person" "1" {:country "India"})
```

Contributed by Sandeep Jagtap.



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
