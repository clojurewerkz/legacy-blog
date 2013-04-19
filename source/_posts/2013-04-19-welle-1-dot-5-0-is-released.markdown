---
layout: post
title: "Welle 1.5.0 is released"
date: 2013-04-19 23:23
comments: false
categories:
  - welle
  - releases
---

## TL;DR

Welle is an expressive [Clojure client for Riak](http://clojureriak.info) with batteries included.

[1.5.0](https://clojars.org/com.novemberain/welle/versions/1.5.0) is a minor release
that is *100% backwards-compatible* with `1.5.x` and introduces several nice features:

 * Retriers for failing operations
 * Conflict resolvers
 * Easier to use update functions

This version has been tested against
Riak `1.2.x` and `1.3.x`.


## Changes between Welle 1.4.0 and 1.5.0

### clojurewerkz.welle.kv/modify

`clojurewerkz.welle.kv/modify` is a new function that combines `clojurewerkz.welle.kv/fetch` and
`clojurewerkz.welle.kv/store` with a user-provided mutation functions. The mutation function
should take a single Riak object as an immutable map and return a modified one.

In case of siblings, a resolver should be used.

`clojurewerkz.welle.kv/modify` will update modification timestamp of the object.

`clojurewerkz.welle.kv/modify` takes the same options as `clojurewerkz.welle.kv/fetch` and
`clojurewerkz.welle.kv/store`


### Conflcit Resolvers

`clojurewerkz.welle.kv/fetch`, and `clojurewerkz.welle.kv/store` now accept a new
option: `:resolver`. Resolvers are basically pure functions that take a collection of
siblings and return a collection of Riak object maps.

Resolvers can be created using
`clojurewerkz.welle.conversion/resolver-from` which takes a function that accepts a collection
of deserialized (unless `fetch` was told otherwise) values and applies any conflict resolution
logic necessary.

`clojurewerkz.welle.kv/fetch-one` now also supports resolvers via the `:resolver` option.
It will raise an exception if siblings are detected and no resolver is provided.



### Retriers

`clojurewerkz.welle.kv/fetch`, `clojurewerkz.welle.kv/fetch-one`, `clojurewerkz.welle.kv/store`,
`clojurewerkz.welle.kv/delete`, and `clojurewerkz.welle.kv/index-query` now retry operations
that fail due to a network issue or any other exception.

By default, the operations will be retrier 3 times. It is possible to provide a custom
retrier using the `:retrier` option. Retriers can be created using
`clojurewerkz.welle.conversion/retrier-from` which takes a function that accepts a callable
(an operation that may need to be retried) and needs to invoke it, handling exceptions
and applying any retrying logic needed.


`clojurewerkz.welle.conversion/counting-retrier` produces a retrier that will retry an operation
given number of times. This is the kind of retrier Welle uses by default.



### Skipping Deserialization for clojurewerkz.welle.kv/fetch

`clojurewerkz.welle.kv/fetch` supports a new boolean option `:skip-deserialize` that allows
automatic deserialization to be skipped.

Contributed by Jonas Tehler.


### Clojure 1.5 By Default

Welle now depends on `org.clojure/clojure` version `1.5.1`. It is
still compatible with Clojure 1.3+ and if your `project.clj` depends
on a different version, it will be used, but 1.5 is the default now.

We encourage all users to upgrade to 1.5, it is a drop-in replacement
for the majority of projects out there.



## Change Log

We recommend all users to upgrade to [1.5.0](https://clojars.org/com.novemberain/welle/versions/1.5.0) a try.

[Welle change log](https://github.com/michaelklishin/welle/blob/master/ChangeLog.md) is available on GitHub.



## Welle is a ClojureWerkz Project

[Welle](http://clojureriak.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](http://clojureneo4j.info), a feature rich idiomatic Clojure client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Welle, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


## Donations

ClojureWerkz [accepts donations](http://clojurewerkz.org/articles/donate.html). If you feel like our projects save you time, consider donating. Thanks.


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
