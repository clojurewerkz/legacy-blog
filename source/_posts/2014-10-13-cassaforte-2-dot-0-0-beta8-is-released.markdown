---
layout: post
title: "Cassaforte 2.0.0-beta8 is released"
date: 2014-10-13 07:37:30 +0400
comments: false
categories:
  - cassaforte
  - releases
---

## TL;DR

[Cassaforte](http://clojurecassandra.info) is a Clojure client for
Apache Cassandra. It is built around CQL 3 and focuses on ease
of use. You will likely find that using Cassandra from Clojure has
never been so easy.

`2.0.0-beta8` is a development release that
introduces a **breaking public API change**.


## Changes between 2.0.0-beta7 and 2.0.0-beta8

`2.0.0-beta8` introduces a major **breaking API change**.

### Query DSL Taken From Hayt 2.0

Cassaforte no longer tries to support query condition DSLs for both Hayt 1.x
and Hayt 2.0. Hayt 2.0 is the only supported flavour now and
is the future.

Some examples of the changes:

``` clojure
;; before
(where :name "Alex")

;; after
(where [[= :name "Alex"]])
(where {:name "Alex"})


;; before
(where :name "Alex" :city "Munich")

;; after
(where [[= :name "Alex"]
        [= :city "Munich"]])
(where {:name "Alex" :city "Munich"})


;; before
(where :name "Alex" :age [> 25])

;; after
(where [[= :name "Alex"]
        [> :age  25]])

;; before
(where :name "Alex" :city [:in ["Munich" "Frankfurt"]])

;; after
(where [[= :name "Alex"]
        [:in :city ["Munich" "Frankfurt"]]])
```

As it's easy to see, the new condition style closer resembles
Clojure itself and thus was a reasonable decision on behalf of Hayt
developers.


## Changes between 2.0.0-beta5 and 2.0.0-beta7

### Hayt Upgraded to 2.0

[Hayt](https://github.com/mpenet/hayt) was upgraded to 2.0.


## Changes between 2.0.0-beta4 and 2.0.0-beta5

### clojurewerkz.cassandra.cql/iterate-table Now Terminates

`clojurewerkz.cassandra.cql/iterate-table` no longer produces an infinite
sequence.


### Keyspace as Option

It is now possible to choose keyspace via an option:

``` clojure
(ns cassaforte.docs
  (:require [clojurewerkz.cassaforte.client :as cc]))

(let [conn (cc/connect {:hosts ["127.0.0.1"] :keyspace "a-keyspace"})]
  )
```

Contributed by Max Barnash (DataStax).


## News and Updates

New releases and updates are announced [on Twitter](http://twitter.com/clojurewerkz). Cassaforte also has [a
mailing list](https://groups.google.com/group/clojure-cassandra), feel
free to ask questions and report issues there.


## Cassaforte is a ClojureWerkz Project

Cassaforte is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [EEP](http://github.com/clojurewerkz/eep), a Clojure library for stream (event) processing
 * [Neocons](http://clojureneo4j.info), a Clojure client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Cassaforte, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz Team](http://twitter.com/clojurewerkz).
