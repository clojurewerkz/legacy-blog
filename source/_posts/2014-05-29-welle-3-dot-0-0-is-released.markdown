---
layout: post
title: "Welle 3.0.0 is released"
date: 2014-05-29 23:06:06 +0400
comments: false
categories:
  - welle
  - releases
---

## TL;DR

Welle is an expressive [Clojure client for Riak](http://clojureriak.info) with batteries included.

[3.0.0](https://clojars.org/com.novemberain/welle/versions/3.0.0) is a
major release that *has [breaking API changes](http://blog.clojurewerkz.org/blog/2014/04/26/major-breaking-public-api-changes-coming-in-our-projects/)*.


## Changes between Welle 2.0.x and 3.0

Welle 3.0 has [breaking API changes](http://blog.clojurewerkz.org/blog/2014/04/26/major-breaking-public-api-changes-coming-in-our-projects/) in most namespaces.

### Client (Connection) is Explicit Argument

All Welle public API functions that issue requests to Riak now require
a client (HTTP or PBC) to be passed as an explicit argument:

``` clojure
(ns welle.docs.examples
  (:require [clojurewerkz.welle.core    :as wc]
            [clojurewerkz.welle.buckets :as wb]
            [clojurewerkz.welle.kv      :as kv])
  (:import com.basho.riak.client.http.util.Constants))

(let [conn   (wc/connect)
      bucket "accounts"
      key    "novemberain"
      val    {:name "Michael" :age 27 :username key}]
  (wb/create conn bucket)
  ;; stores data serialized as JSON
  (kv/store conn bucket key val {:content-type Constants/CTYPE_JSON_UTF8})
  ;; fetches it back
  (kv/fetch conn bucket key))
```

### Options as Maps

Functions that take optional arguments now require them to be proper maps
(and not pseudo-keywords):

``` clojure
;; in 2.0
(kv/store bucket key val :content-type Constants/CTYPE_JSON_UTF8)

;; in 3.0
(kv/store conn bucket key val {:content-type Constants/CTYPE_JSON_UTF8})
```

### HTTPComponents 4.3

Welle now excludes HTTPComponents dependency for Riak client and instead
uses version 4.3 which `clj-http` depends on.



## Change Log

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
