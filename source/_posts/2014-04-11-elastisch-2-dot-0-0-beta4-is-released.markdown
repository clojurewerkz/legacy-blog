---
layout: post
title: "Elastisch 2.0.0-beta4 is released"
date: 2014-04-11 03:18:57 +0400
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

[2.0.0-beta4](https://clojars.org/clojurewerkz/elastisch/versions/2.0.0-beta4)
is a preview release of Elastisch 2.0, which focuses on the new
features in ElasticSearch 1.0 and 1.1 as well as some API refinements.


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



## Full Change Log

[Elastisch change log](https://github.com/clojurewerkz/elastisch/blob/master/ChangeLog.md) is available on GitHub.


## Thank You, Contributors

Kudos to Halit Olali, shmish111, and Richie Vos for contributing to this release.


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
