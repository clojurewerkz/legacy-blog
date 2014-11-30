---
layout: post
title: "Cassaforte 2.0.0-rc2 is released"
date: 2014-11-30 21:50:37 +0300
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

`2.0.0-rc2` is a release candidate for 2.0.


## Changes between 2.0.0-rc1 and 2.0.0-rc2

### Fixes Race Condition in Async Operations

Async database operations no longer suffer from a race condition between
issueing them and definiting callbacks on the returned future value.

Contributed by Kirill Chernyshov.

### Compression Option

`:compression` is a new option that can be used when connecting:

``` clojure
(require '[clojurewerkz.cassaforte.client :as client])

(let [s (client/connect ["127.0.0.1"] "my-keyspace" {:compression :snappy})]
  )
```

Valid compression values are:

 * `:snappy`
 * `:lz4`
 * `:none` (or `nil`)

Contirbuted by Max Barnash (DataStax).



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
