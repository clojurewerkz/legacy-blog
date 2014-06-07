---
layout: post
title: "Cassaforte 2.0.0-beta1 is released"
date: 2014-06-07 23:31:37 +0400
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

`2.0.0` is a major API revision release that introduces [breaking public API changes](http://blog.clojurewerkz.org/blog/2014/04/26/major-breaking-public-api-changes-coming-in-our-projects/).


## Changes between 1.3.0 and 2.0.0

Cassaforte 2.0 has [breaking API changes](http://blog.clojurewerkz.org/blog/2014/04/26/major-breaking-public-api-changes-coming-in-our-projects/) in most namespaces.

### Client (Session) is Explicit Argument

All Cassaforte public API functions that issue requests to Cassandra now require
a client (session) to be passed as an explicit argument:

```clj
(ns cassaforte.docs
  (:require [clojurewerkz.cassaforte.client :as cc]
            [clojurewerkz.cassaforte.cql    :as cql]))

(let [conn (cc/connect ["127.0.0.1"])]
  (cql/use-keyspace conn "cassaforte_keyspace"))
```

```clj
(ns cassaforte.docs
  (:require [clojurewerkz.cassaforte.client :as cc]
            [clojurewerkz.cassaforte.cql    :as cql]
            [clojurewerkz.cassaforte.query :refer :all]))

(let [conn (cc/connect ["127.0.0.1"])]
  (cql/create-table conn "user_posts"
                (column-definitions {:username :varchar
                                     :post_id  :varchar
                                     :body     :text
                                     :primary-key [:username :post_id]})))
```

```clj
(ns cassaforte.docs
  (:require [clojurewerkz.cassaforte.client :as cc]
            [clojurewerkz.cassaforte.cql    :as cql]))

(let [conn (cc/connect ["127.0.0.1"])]
  (cql/insert conn "users" {:name "Alex" :age (int 19)}))
```

### Policy Namespace

Policy-related functions from `clojurewerkz.cassaforte.client` were extracted into
`clojurewerkz.cassaforte.policies`:

```clojure
(require '[clojurewerkz.cassaforte.policies :as cp])

(cp/exponential-reconnection-policy 100 1000)
```

``` clojure
(require '[clojurewerkz.cassaforte.policies :as cp])

(let [p (cp/round-robin-policy)]
  (cp/token-aware-policy p))
```


### Cassandra Sessions Compatible with with-open

`Session#shutdown` was renamed to `Session#close` in
cassandra-driver-core. Cassaforte needs to be adapted to that.

Contributed by Jarkko Mönkkönen.



## News and Updates

New releases and updates are announced [on
Twitter](http://twitter.com/clojurewerkz). Cassaforte also has [a
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
