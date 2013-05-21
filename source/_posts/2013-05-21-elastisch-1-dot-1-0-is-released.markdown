---
layout: post
title: "Elastisch 1.1.0 is released"
date: 2013-05-21 23:58
comments: false
categories: 
  - elastisch
  - releases
---

## TL;DR

Elastisch is a battle tested, small but feature rich and well documented [Clojure client for ElasticSearch](http://clojureelasticsearch.info).
It supports virtually every Elastic Search feature and has [solid documentation](http://clojureelasticsearch.info).

[1.1.0](https://clojars.org/clojurewerkz/elastisch/versions/1.1.0)
includes several new features, most notably a native client with the
same API as the REST one Elastisch already has.


## Supported ElasticSearch Versions

Elastisch 1.1's native client requires [ElasticSearch
0.90.0](http://www.elasticsearch.org/2013/04/29/0-90-0-released/). ElasticSearch
still evolves rapidly and binary protocol changes quite often, so the
version match between the client and the server is currently a
requirement for binary clients.

This restriction does not apply to REST API clients.


## Changes in 1.1.0

### Native Client

Elastisch `1.1.0` includes a major new feature: native ElasticSearch client.
The client uses ElasticSearch's Java API, and can be used with
both transport and node clients.

#### Rationale

Native client is more bandwidth efficient. It also can use SMILE (binary JSON format) to be more
efficient on the wire.

#### Namespace Layout

Native client API in Elastisch is nearly identical to that of the REST API client
and resides in `clojurewerkz.elastisch.native` and `clojurewerkz.elastisch.native.*`
namespaces (similarly to how `clojurewerkz.elastisch.rest` `clojurewerkz.elastisch.rest.*`
namespaces are organized).

#### Connections

Transport client (used for TCP/remote connections) connections are set up using
`clojurewerkz.elastisch.native/connect!`. Note that you need to provide node
configuration that at least has cluster name in it:

``` clojure
(require '[clojurewerkz.elastisch.native :as es])

;; note that transport client uses port 9300 by default.
;; it also can connect to multiple cluster nodes
(es/connect! [["127.0.0.1" 9300]]
             {"cluster.name" "elasticsearch_antares" })
```
Cluster name and transport node addresses can be retrieved via HTTP API, for example:

```
curl http://localhost:9200/_cluster/nodes
{"ok":true,"cluster_name":"elasticsearch_antares","nodes":...}}
```

#### Performing Operations

The Native client tries to be as close as possible to the existing REST client API.
For example, document operation functions in `clojurewerkz.elastisch.native.document`,
such as `clojurewerkz.elastisch.native.document/create`,
follow `clojurewerkz.elastisch.rest.document` function signatures as closely as
possible:

``` clojure
;; in the REPL
(require '[clojurewerkz.elastisch.native :as es])
(require '[clojurewerkz.elastisch.native.document :as doc])

(es/connect! [["127.0.0.1" 9300]]
             {"cluster.name" "elasticsearch_antares" })

(doc/put index-name index-type id document)
(doc/get index-name index-type id)
```

The same with returned results. Note, however, that ES transport client
does have (very) minor differences with the REST API and it is not always possible
for Elastisch to completely cover such differences.

#### Async Operations

Native client offers a choice of synchronous (blocking calling thread until a response
is received) and asynchronous (returns a future) versions of multiple API operations:

``` clojure
;; in the REPL
(require '[clojurewerkz.elastisch.native :as es])
(require '[clojurewerkz.elastisch.native.document :as doc])

(es/connect! [["127.0.0.1" 9300]]
             {"cluster.name" "elasticsearch_antares" })

(doc/put index-name index-type id document)

;; returns a response
(doc/get index-name index-type id)
;; returns a future that will eventually
;; contain a response
(doc/async-get index-name index-type id)
```

One notable exception to this is administrative operations (such as opening or closing
an index). The rationale for this is that they are rarely executed on the hot
code path (e.g. in tight loops), so convenience and better error visibility is more
important for them.

GH issues: #17, #18, #20.


### Clojure 1.5 By Default

Elastisch now depends on `org.clojure/clojure` version `1.5.0`. It is still compatible with Clojure 1.3+ and if your `project.clj` depends
on 1.3 or 1.4, it will be used, but 1.5 is the default now.

We encourage all users to upgrade to 1.5, it is a drop-in replacement for the majority of projects out there.


### Bulk Request Support

Bulk requests are now supported. All the relevant code is in the `clojurewerkz.elastisch.rest.bulk`
namespace. Here is a small example of bulk document indexing using this new API:

``` clojure
(require '[clojurewerkz.elastisch.rest.bulk :as eb])

(eb/bulk (eb/bulk-index doc1 doc2 doc3) :refresh true)
```

Contributed by Davie Moston.


### Scroll Queries Support

Scroll queries are now easier to perform thanks to the new `clojurewerkz.elastisch.rest.document/scroll`
function that takes a scroll id and amount of time retrieved documents and related information
will be kept in memory for future retrieval. They are analogous to database cursors.

A short code example:

``` clojure
(require '[clojurewerkz.elastisch.rest.document :as doc])
(require '[clojurewerkz.elastisch.query :as q])
(require '[clojurewerkz.elastisch.rest.response :refer [hits-from]])

(let [index-name   "articles"
      mapping-type "article"
      response     (doc/search index-name mapping-type
                               :query (q/query-string :query "*")
                               :search_type "scan"
                               :scroll "1m"
                               :size 1)
      scroll-id     (:_scroll_id response)
      scan-response (doc/scroll scroll-id :scroll "1m")
      scan-hits     (hits-from scan-response)]
  (println scan-hits))
```

Contributed by Davie Moston.


### Cheshire Update

[Cheshire](https://github.com/dakrone/cheshire/) dependency has been upgraded to version `5.1.1`.

### clj-http Update

[clj-http](https://github.com/dakrone/clj-http/) dependency has been upgraded to version `0.7.2`.

### Count API No Longer Ignores Mapping Types

`clojurewerkz.elastisch.rest.document/count` no longer ignores mapping types.

GH issue: #6.


### Count API now uses GET requests

`clojurewerkz.elastisch.rest.document/count` now correctly uses `GET` for requests without
the query part and`POST` for request that have it.

GH issue: #5.



### Updates With Scripts

`clojurewerkz.elastisch.rest.document/update-with-script` is a new function
that updates a document with a provided script:

``` clojure
(require '[clojurewerkz.elastisch.rest.document :as doc])

;; initializes a counter at 1
(doc/update-with-script index-name mapping-type "1"
      "ctx._source.counter = 1")

;; increments the counter by 4
(doc/update-with-script index-name mapping-type "1"
      "ctx._source.counter += inc"
      {"inc" 4})
```

`clojurewerkz.elastisch.native.document/update-with-script` is the native
client counterpart that takes the same arguments.



## Change Log

[Elastisch change log](https://github.com/clojurewerkz/elastisch/blob/master/ChangeLog.md) is available on GitHub.


## Thank You, Contributors

Kudos to Davie Moston, Andrew Jones, Jon Pither and Antonio Terreno who contributed to this release.


## Elastisch is a ClojureWerkz Project

[Elastisch](http://clojureelasticsearch.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Elastisch, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
