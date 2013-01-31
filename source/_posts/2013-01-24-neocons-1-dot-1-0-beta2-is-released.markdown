---
layout: post
title: "Neocons 1.1.0-beta2 is released"
date: 2013-01-24 16:36
comments: false
categories:
  - releases
  - neocons
---

## TL;DR

Neocons is a feature rich idiomatic [Clojure client for the Neo4J REST API](http://clojureneo4j.info).

`1.1.0-beta2` is second preview `1.1.0` release that is *100% backwards-compatible* with `1.0.x`.



## Changes between Neocons 1.1.0-beta1 and 1.1.0-beta2

### Support upgraded to 0.10.0

Neocons now uses ClojureWerkz Support 0.10.0.


### clj-http upgraded to 0.6.3

Neocons now uses clj-http 0.6.3.


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


## Changes between Neocons 1.0.0 and 1.1.0-beta1

### Initial Spatial Plugin Support

Neocons now has initial support for the Neo4J Spatial plugin in the `clojurewerkz.neocons.spatial`
namespace.

Contributed by Kyle Goodwin.


### Cheshire For JSON Serliazation

Neocons now uses (and depends on) [Cheshire](https://github.com/dakrone/cheshire) for JSON serialization.
[clojure.data.json](https://github.com/clojure/data.json) is no longer a dependency.

### Clojure 1.4 By Default

Neocons now depends on `org.clojure/clojure` version `1.4.0`. It is still compatible with Clojure 1.3 and if your `project.clj` depends
on 1.3, it will be used, but 1.4 is the default now.

We encourage all users to upgrade to 1.4, it is a drop-in replacement for the majority of projects out there.


### Pass Configuration When Creating Node Indexes

`clojurewerkz.neocons.rest.nodes/create-index` now correctly passes index configuration
to Neo4J Server. Reported in #6.


### clj-http upgraded to 0.5.5

Neocons now uses clj-http 0.5.5.




## Change Log

We recommend all users to give [1.1.0-beta2](https://clojars.org/clojurewerkz/neocons/versions/1.1.0-beta2) a try.

[Neocons change log](https://github.com/michaelklishin/neocons/blob/master/ChangeLog.md) is available on GitHub.



## Neocons is a ClojureWerkz Project

[Neocons](http://clojureneo4j.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](https://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](https://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Monger](https://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Welle](https://clojureriak.info), a Riak client with batteries included
 * [Quartzite](https://clojurequartz.info), a powerful scheduling library

and several others. If you like Neocons, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
