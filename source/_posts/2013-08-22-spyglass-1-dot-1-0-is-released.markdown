---
layout: post
title: "Spyglass 1.1.0 is released"
date: 2013-08-22 23:09
comments: false
categories:
  - spyglass
  - releases
---

## TL;DR

Spyglass is a very fast [Clojure client for
Memcached](http://clojurememcached.info) (as well as Couchbase and
Kestrel) built on top of
[SpyMemcached](http://code.google.com/p/spymemcached/).

`1.1.0` is a minor release that introduces several minor features
and*has breaking changes*.


## Changes between 1.0.0 and 1.1.0

### Clojure 1.4 Requirement

Spyglass `1.1.0` **drops support for Clojure 1.3**.


### Heroku Add-on Support

By using SpyMemcached `2.8.9`, you now can use Spyglass with Heroku
Memcached add-ons:

``` clojure
(defproject my-great-project "0.1.0-SNAPSHOT"
  :dependencies [[org.clojure/clojure "1.5.1"]
                 [clojurewerkz/spyglass "1.1.0-beta6-SNAPSHOT"
                  :exclusions [spy/spymemcached]]
                 [spy/spymemcached "2.8.9"]]
  :repositories {"spy-memcached" {:url "http://files.couchbase.com/maven2/"}})
```

Contributed by Connor Mendenhall.


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


### SASL (Authentication) Support

`clojurewerkz.spyglass.client/text-connection` and `clojurewerkz.spyglass.client/bin-connection`
now support credentials:

(ns my.service
  (:require [clojurewerkz.spyglass.client :as c]))

;; uses credentials from environment variables, e.g. on Heroku:
(c/text-connection "127.0.0.1:11211" (System/getenv "MEMCACHE_USERNAME")
                                     (System/getenv "MEMCACHE_PASSWORD"))

When you need to fine tune things and want to use a custom connection factory, you need
to instantiate *auth descriptor* and pass it explicitly, like so:

``` clojure
(ns my.service
  (:require [clojurewerkz.spyglass.client :as c])
  (:import [net.spy.memcached.auth AuthDescriptor]))

(let [ad (AuthDescriptor/typical (System/getenv "MEMCACHE_USERNAME")
                                 (System/getenv "MEMCACHE_PASSWORD"))]
  (c/text-connection "127.0.0.1:11211" (c/text-connection-factory :failure-mode :redistribute
                                                                  :aut-descriptor ad)))
```

### Blocking Deref for Futures

Futures returned by async Spyglass operations now implement "blocking dereferencing":
they can be dereferenced with a timeout and default value, just like futures created
with `clojure.core/future` and similar.

Contributed by Joseph Wilk.



### Support For Configurable Connections

New functions `clojurewerkz.spyglass.client/text-connection-factory` and
`clojurewerkz.spyglass.client/bin-connection-factory` provide a Clojuric
way of instantiating connection factories. Those factories, in turn, can be
passed to new arities of `clojurewerkz.spyglass.client/text-connection` and
`clojurewerkz.spyglass.client/bin-connection` to control failure mode,
default transcoder and so on:

``` clojure
(ns my.service
  (:require [clojurewerkz.spyglass.client :as c]))

(c/text-connection "127.0.0.1:11211" (c/text-connection-factory :failure-mode :redistribute))
```


### core.cache Implementation

`clojurewerkz.spyglass.cache` now provides a `clojure.core.cache` implementation on top of
Memcached:

``` clojure
(ns my.service
  (:require [clojurewerkz.spyglass.client :as sg]
            [clojurewerkz.spyglass.cache  :as sc]
            [clojure.core.cache           :as cc]))

(let [client (sg/text-connection)
      cache  (sc/sync-spyglass-cache-factory)]
      (cc/has? cache "a-key")
      (cc/lookup cache "a-key"))
```

`SyncSpyglassCache` uses synchronous operations from `clojurewerkz.spyglass.client`. Asynchronous implementation
that returns futures will be added in the future.


### SpyMemcached 2.8.10

SpyMemcached has been upgraded to `2.8.10`.


### Improved Couchbase Support

`clojurewerkz.spyglass.couchbase/connection` is a new function that connects to Couchbase with the given
bucket and credentials. It returns a client that regular `clojurewerkz.spyglass.memcached` functions can
use.




## Change Log

We recommend all users to give [1.1.0](https://clojars.org/clojurewerkz/spyglass/versions/1.1.0) a try.

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
