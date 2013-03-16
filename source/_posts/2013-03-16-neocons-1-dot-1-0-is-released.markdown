---
layout: post
title: "Neocons 1.1.0 is released"
date: 2013-03-16 22:26
comments: false
categories:
  - neocons
  - releases
---

## TL;DR

Neocons is a feature rich idiomatic [Clojure client for the Neo4J REST API](http://clojureneo4j.info).

`1.1.0` is a minor release that includes several minor improvements and
bug fixes and is *100% backwards-compatible* with `1.0.x`.



## Changes between Neocons 1.0.x and 1.1.0

### ClojureWerkz Support Upgrade

Neocons now uses ClojureWerkz Support 0.15.0.


### Correct URI Path Encoding

Neocons now correctly encodes all parts of URIs, which means
index keys and values can contain whitespace and Unicode
characters, for example.

Keys with colons are now handled correctly (as of Urly `2.0.0-alpha5`).

GH issue: #20

### clj-http Upgrade

Neocons now uses clj-http 0.6.4.


### clojurewerkz.neocons.rest.relationship/maybe-create Now Fully Supports Ids

`clojurewerkz.neocons.rest.relationship/maybe-create` now correctly works with node ids
as well as `Node` records.

GH issue: #19.

### More Informative Exceptions

HTTP exceptions bubbling up now will carry more information (namely the response `:body`).

Contributed by Adrian Gruntkowski.


### clojurewerkz.neocons.rest.relationships/get-many

`clojurewerkz.neocons.rest.relationships/get-many` is a new function that fetches multiple relationships
by id in a single request:

```clojure
(require '[clojurewerkz.neocons.rest.relationships :as rel])

(rel/get-many [id1 id2 id3])
```

Contributed by Adrian Gruntkowski.


### Initial Spatial Plugin Support

Neocons now has initial support for the Neo4J Spatial plugin in the `clojurewerkz.neocons.spatial`
namespace.

Contributed by Kyle Goodwin.


### Cheshire For JSON Serliazation

Neocons now uses (and depends on) [Cheshire](https://github.com/dakrone/cheshire) for JSON serialization.
[clojure.data.json](https://github.com/clojure/data.json) is no longer a dependency.


### Pass Configuration When Creating Node Indexes

`clojurewerkz.neocons.rest.nodes/create-index` now correctly passes index configuration
to Neo4J Server. Reported in #6.




## Change Log

We recommend all users to upgrade to [1.1.0](https://clojars.org/clojurewerkz/neocons/versions/1.1.0) a try.

[Neocons change log](https://github.com/michaelklishin/neocons/blob/master/ChangeLog.md) is available on GitHub.



## Neocons is a ClojureWerkz Project

[Neocons](http://clojureneo4j.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Neocons, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
