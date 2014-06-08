---
layout: post
title: "Elastisch 2.0.0-rc1 is released"
date: 2014-04-26 19:18:16 +0400
comments: false
categories:
  - elastisch
  - releases
---

## TL;DR

Elastisch is a battle tested, small but feature rich and well
documented [Clojure client for
ElasticSearch](http://clojureelasticsearch.info). It supports
virtually every Elastic Search feature and has [solid
documentation](http://clojureelasticsearch.info).

[2.0.0-rc1](https://clojars.org/clojurewerkz/elastisch/versions/2.0.0-rc1)
is a release candidate of Elastisch 2.0, which focuses on the new
features in ElasticSearch 1.1 and introduces major API improvements,
including a **breaking change**.


## Changes between Elastisch 2.0.0-beta5 and 2.0.0-rc1

### Connection/Client As Explicit Argument

Starting with Elastisch `2.0.0-rc1`, connection (client) is no longer a shared
dynamic var but rather is an explicit argument that relevant API functions
accept.

Before the change:

``` clojure
(ns clojurewerkz.elastisch.docs.examples
  (:require [clojurewerkz.elastisch.rest  :as esr]
            [clojurewerkz.elastisch.rest.index :as esi]
            [clojurewerkz.elastisch.rest.document :as esd]))

(defn -main
  [& args]
  (esr/connect! "http://127.0.0.1:9200")
  (let [mapping-types {"person" {:properties {:username   {:type "string" :store "yes"}
                                              :first-name {:type "string" :store "yes"}
                                              :last-name  {:type "string"}
                                              :age        {:type "integer"}
                                              :title      {:type "string" :analyzer "snowball"}
                                              :planet     {:type "string"}
                                              :biography  {:type "string" :analyzer "snowball" :term_vector "with_positions_offsets"}}}}
        doc           {:username "happyjoe" :first-name "Joe" :last-name "Smith" :age 30 :title "Teh Boss" :planet "Earth" :biography "N/A"}]
    (esi/create "myapp2_development" :mappings mapping-types)
    (esd/create "myapp2_development" "person" doc)))
```

After the change:

``` clojure
(ns clojurewerkz.elastisch.docs.examples
  (:require [clojurewerkz.elastisch.rest  :as esr]
            [clojurewerkz.elastisch.rest.index :as esi]
            [clojurewerkz.elastisch.rest.document :as esd]))

(defn -main
  [& args]
  (let [conn          (esr/connect "http://127.0.0.1:9200")
        mapping-types {"person" {:properties {:username   {:type "string" :store "yes"}
                                              :first-name {:type "string" :store "yes"}
                                              :last-name  {:type "string"}
                                              :age        {:type "integer"}
                                              :title      {:type "string" :analyzer "snowball"}
                                              :planet     {:type "string"}
                                              :biography  {:type "string" :analyzer "snowball" :term_vector "with_positions_offsets"}}}}
        doc           {:username "happyjoe" :first-name "Joe" :last-name "Smith" :age 30 :title "Teh Boss" :planet "Earth" :biography "N/A"}]
    (esi/create conn "myapp2_development" :mappings mapping-types)
    (esd/create conn "myapp2_development" "person" doc)))
```

Dynamic var reliance has been a [major
complaint](http://stuartsierra.com/2013/03/29/perils-of-dynamic-scope)
of Clojure users for quite some time and 2.0 is the right time to fix
this.


## Changes between Elastisch 2.0.0-beta4 and 2.0.0-beta5

### Response Helpers Compatible With ES 1.1

`clojurewerkz.elastisch.rest.response/created?` and `clojurewerkz.elastisch.native.response/created?`
were adapted for recent ES releases.

Contributed by Oliver McCormack (The Climate Corporation).

### ElasticSearch Client Update

ElasticSearch client has been upgraded to `1.1.1`.


## Changes between Elastisch 2.0.0-beta3 and 2.0.0-beta4

### Options As Maps

Elastisch has tranditionally accepted options as (pseudo) keywrod
arguments, e.g.

``` clojure
(doc/search index-name mapping-type :query (q/term :biography "say"))
```

Starting with `2.0.0-beta4`, passing a single map of arguments
is now also supported by nearly all document, index, admin and percolation
functions:

``` clojure
(doc/search index-name mapping-type {:query (q/term :biography "say")})
```

As a new design rule, all new API elements (e.g. aggregations) will accept a single map
of options.

GH issue: #59.

### Percolation of Existing Documents (REST API)

REST API client now supports percolation of existing documents:

``` clojure
(require '[clojurewerkz.elastisch.rest.percolation :as pcl])

(pcl/percolate-existing "articles" "article" "123")
```



## Changes between Elastisch 2.0.0-beta2 and 2.0.0-beta3

### ElasticSearch Client Update

ElasticSearch client has been upgraded to `1.1.0`.

### Clojure 1.6

Elastisch now depends on `org.clojure/clojure` version `1.6.0`. It is
still compatible with Clojure 1.4 and if your `project.clj` depends on
a different version, it will be used, but 1.6 is the default now.

### Type Exists Operation

[types-exists](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/indices-types-exists.html) support
in both rest and native clients:

``` clojure
(require '[clojurewerkz.elastisch.rest.index :as esi])

(esi/type-exists? "an-index" "a-type")
```

Contributed by Halit Olali.

## Changes between Elastisch 2.0.0-beta1 and 2.0.0-beta2

### (Improved) Aggregation Support

Elastisch 2.0 features multiple convenience functions for working with
[ElasticSearch aggregations](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/search-aggregations.html).

`clojurewerkz.elastisch.aggregation` is a new namespace that contains
helper functions that produce various types of aggregations. Just like
`clojurewerkz.elastisch.query`, all of the functions return maps and
are optional.

`clojurewerkz.elastisch.rest.response/aggregations-from` is a new function
that returns aggregations from a search response:

``` clojure
(require '[clojurewerkz.elastisch.rest.document :as doc])
(require '[clojurewerkz.elastisch.query :as q])
(require '[clojurewerkz.elastisch.aggregation :as a])
(require '[clojurewerkz.elastisch.rest.response :refer [aggregations-from]])

(let [index-name   "people"
        mapping-type "person"
        response     (doc/search index-name mapping-type
                                 :query (q/match-all)
                                 :aggregations {:min_age (a/min "age")})
        agg          (aggregation-from response :min_age)]
    (is (= {:value 22.0} agg)))
```

Aggregations support is primarily focused on REST client at the moment.

### clj-http Update

[clj-http](https://github.com/dakrone/clj-http/) dependency has been upgraded to version `0.9.1`.


## Changes between Elastisch 1.4.0 and 2.0.0-beta1

### ElasticSearch 1.0 Compatibility

Main goal of Elastisch 2.0 is ElasticSearch 2.0 compatibility. This includes minor
API changes (in line with [ElasticSearch 1.0 API and terminology changes](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/breaking-changes.html))
and moderate internal modifications.


### Support for cluster nodes stats and info REST APIs

`clojureworkz.elastisch.rest.admin/nodes-info` and `clojureworkz.elastisch.rest.admin/nodes-stats`
are new administrative functions that provide access to ElasticSearch
[cluster stats and node info](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/cluster-nodes-info.html).

Examples:

``` clojure
(require '[clojurewerkz.elastisch.rest.admin :as admin])

(admin/nodes-stats)
(admin/nodes-stats :nodes "_all")
(admin/nodes-stats :nodes ["node1" "node2"] ["indices" "os" "plugins"])

(admin/nodes-info)
(admin/nodes-info :nodes "_all")
(admin/nodes-info :nodes ["node1" "node2"] ["indices" "os" "plugins"])
```

See [ElasticSearch nodes stats
documentation](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/cluster-nodes-stats.html),
[nodes info
page](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/cluster-nodes-info.html),
and [node specification
page](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/cluster.html#cluster-nodes)
for more info.

Contributed by Joachim De Beule.

### Support for _cluster/state REST API

Added `(clojureworkz.elastisch.rest.admin/cluster-state & {:as params})`

Examples:

``` clojure
(require '[clojurewerkz.elastisch.rest.admin :as admin])

(admin/cluster-state)
(admin/cluster-state :filter_nodes true)
```

See [ElasticSearch documentation](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/cluster-state.html) for more info.

Contributed by Joachim De Beule.


### Support for _cluster/health REST API

Added `(clojureworkz.elastisch.rest.admin/cluster-health & {:as params})`

Example:

``` clojure
(require '[clojurewerkz.elastisch.rest.admin :as admin])

(admin/cluster-health)
(admin/cluster-health :index "index1")
(admin/cluster-health :index ["index1","index2"])
(admin/cluster-health :index "index1" :pretty true :level "indices")
```

See [ElasticSearch documentation](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/cluster-health.html) for more info.

Contributed by Joachim De Beule.


### Support for analyze in REST API client

Added `(doc/analyze text & {:as params})`

See [ElasticSearch documentation](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/indices-analyze.html) for more info.

Examples:

``` clojure
(require '[clojurewerkz.elastisch.rest.document :as doc])

(doc/analyze "foo bar baz")
(doc/analyze "foo bar baz" :index "some-index-name")
(doc/analyze "foo bar baz" :analyzer "whitespace")
(doc/analyze "foo bar baz" :tokenizer "keyword" :filters "lowercase")
(doc/analyze "foo bar baz" :index "some-index-name" :field "some-field-name")
```

Contributed by Joachim De Beule


### Query String Escaping

`clojurewerkz.elastisch.query/query-string` accepts a new option, `:escape-with`,
which is a function that performs escaping of special characters in query string
queries.

By default `clojurewerkz.elastisch.escape/escape-query-string-characters` is used.

Contributed by Ben Reinhart (Groupon).


### ElasticSearch Native Client Upgrade

Elastisch now depends on ElasticSearch native client version `1.0.1`.


### clj-http Update

[clj-http](https://github.com/dakrone/clj-http/) dependency has been upgraded to version `0.9.0`.


## Full Change Log

[Elastisch change log](https://github.com/clojurewerkz/elastisch/blob/master/ChangeLog.md) is available on GitHub.


## Thank You, Contributors

Kudos to Halit Olali, shmish111, and Richie Vos for contributing to
the 2.0 release.


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
