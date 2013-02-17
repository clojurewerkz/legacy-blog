---
layout: post
title: "'Spyglass 1.1.0-beta2 is released'"
date: 2013-01-31 18:58
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

`1.1.0-beta2` is second preview `1.1.0` release that is *100%
backwards-compatible* with `1.0.x`.


## Changes between 1.1.0-beta1 and 1.1.0-beta2

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



## Changes between 1.0.0 and 1.1.0-beta1

### Blocking Deref for Futures

Futures returned by async Spyglass operations now implement "blocking dereferencing":
they can be dereferenced with a timeout and default value, just like futures created
with `clojure.core/future` and similar.

Contributed by [Joseph Wilk](https://github.com/josephwilk).



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

`SyncSpyglassCache` uses synchronous operations from `clojurewerkz.spyglass.client`.
Asynchronous implementation that returns futures will be added in the future.


### SpyMemcached 2.8.4

SpyMemcached has been upgraded to `2.8.4`.


### Improved Couchbase Support

`clojurewerkz.spyglass.couchbase/connection` is a new function that
connects to Couchbase with the given bucket and credentials. It
returns a client that regular `clojurewerkz.spyglass.memcached`
functions can use.


### Clojure 1.4 By Default

Spyglass now depends on `org.clojure/clojure` version `1.4.0`. It is
still compatible with Clojure 1.3 and if your `project.clj` depends on
1.3, it will be used, but 1.4 is the default now.

We encourage all users to upgrade to 1.4, it is a drop-in replacement for the majority of projects out there.




## Change Log

We recommend all users to give [1.1.0-beta2](https://clojars.org/clojurewerkz/spyglass/versions/1.1.0-beta2) a try.

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
