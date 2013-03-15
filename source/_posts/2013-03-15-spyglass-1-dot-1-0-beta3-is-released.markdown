---
layout: post
title: "Spyglass 1.1.0-beta3 is released"
date: 2013-03-15 22:51
comments: false
categories:
  - releases
  - spyglass
---

## TL;DR

Spyglass is a very fast [Clojure client for
Memcached](http://clojurememcached.info) (as well as Couchbase and
Kestrel) built on top of
[SpyMemcached](http://code.google.com/p/spymemcached/).

`1.1.0-beta3` is a preview release that *has breaking changes* in
`clojurewerkz.spyglass.cache`.


## Changes between 1.1.0-beta2 and 1.1.0-beta3

### Clojure 1.5 By Default

Spyglass now depends on `org.clojure/clojure` version `1.5.1`. It is
still compatible with Clojure 1.3+ and if your `project.clj` depends
on a different version, it will be used, but 1.5 is the default now.

We encourage all users to upgrade to 1.5, it is a drop-in replacement
for the majority of projects out there.

### Asynchronous Cache Store

Spyglass now ships both sync and async implementations of [clojure.core.cache](https://github.com/clojure/core.cache).

To instantiate async store, use `clojurewerkz.spyglass.cache/async-spyglass-cache-factory`.
`clojurewerkz.spyglass.cache/spyglass-cache-factory` was renamed to `clojurewerkz.spyglass.cache/sync-spyglass-cache-factory`.

Contributed by [Joseph Wilk](https://github.com/josephwilk).

### Fix Authentication Support

`clojurewerkz.spyglass.client/text-connection` and `clojurewerkz.spyglass.client/bin-connection`
no longer fail when credentials are passed in.


### Empty gets Responses

`clojurewerkz.spyglass.client/gets` now correctly handles responses for
keys that do not exist.

GH issue: #4.




## Change Log

We recommend all users to give [1.1.0-beta3](https://clojars.org/clojurewerkz/spyglass/versions/1.1.0-beta3) a try.

[Spyglass change log](https://github.com/clojurewerkz/spyglass/blob/master/ChangeLog.md) is available on GitHub.



## Spyglass is a ClojureWerkz Project

[Spyglass](http://clojurememcached.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](http://clojureneo4j.info), a feature rich idiomatic Clojure client for the Neo4J REST API * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Spyglass, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
