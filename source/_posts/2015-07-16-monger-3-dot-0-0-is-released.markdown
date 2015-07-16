---
layout: post
title: "Monger 3.0.0 is released"
date: 2015-07-16 23:39:05 +0300
comments: false
categories:
  - monger
  - releases
  - mongodb
---

## TL;DR

Monger is an idiomatic [Clojure MongoDB driver](http://clojuremongodb.info) for a more civilized age.
It has batteries included, offers powerful expressive query DSL, strives to support every MongoDB 2.0+ feature and has sane defaults.
It also has [solid documentation](http://clojuremongodb.info).

`3.0.0` is a major release based on [version `3.0` of the MongoDB Java driver](https://www.mongodb.com/blog/post/introducing-30-java-driver).

We are only getting started with migrating to the 3.0 Java
driver. This release focuses on removing Monger API elements that are
no longer available. There are quite a few impovements that Monger
can use: more efficient serislisation API, asynchronous API, and so on.
Monger will make use of those in future `3.x` releases.

We'd like to thank [Jeff Yemin](https://twitter.com/jeffyemin) and
[Ross Lawley](https://twitter.com/rossc0) from MongoDB for helping us
migrate, sharing Java client roadmap, and answering our endless
questions. Monger 3.0 would ship months later if this wasn't for them.


## Changes between 2.1.0 and 3.0.0

Monger 3.0 is based on the [MongoDB Java driver 3.0](https://www.mongodb.com/blog/post/introducing-30-java-driver)
and has some (relatively minor) **breaking API changes**.

### Error Handling Built Around Write Concerns

Monger no longer provides `monger.core/get-last-error`. It is no
longer needed: write concerns and exceptions is now the primary way for clients
to be notified of operation failures.

### New Authentication API

MongoDB 3.0 supports different authentication mechanisms. Multiple
credentials can be specified for a single connection. The client
and the server then can negotiate what authentication mechanism to use
and which set of credentials succeed.

Monger introduces a new namespace for credential instantiation:
`monger.credentials`. The most common function that relies on
authentication mechanism negotiation is `monger.credentials/for`:

``` clojure
(require '[monger.core :as mg])
(require '[monger.credentials :as mcr])

(let [creds (mcr/for "username" "db-name" "pa$$w0rd")
      conn  (mg/connect-with-credentials "127.0.0.1" creds)]
      )
```

`mg/connect-with-credentials` is the most convenient function to
connect with if you plan on using authentication.

When connecting using a URI, the API hasn't changed.

### monger.search is Gone

`monger.search` is gone. MongoDB 3.0 supports search queries
using regular query operators, namely `$text`. `monger.operators` is
extended to include `$text`, `$search`, `$language`, and `$natural`.

An example of a search query in 3.0:

``` clojure
(require '[monger.core :as mg])
(require '[monger.credentials :as mcr])
(require '[monger.collection :as mc])
(require '[monger.operators :refer [$text $search]])

(let [creds (mcr/for "username" "db-name" "pa$$w0rd")
      conn  (mg/connect-with-credentials "127.0.0.1" creds)
      db    (mg/get-db conn "db-name")]
  (mc/find-maps db "collection" {$text {$search "hello"}}))
```


### JSON Serialization of BSON Timestamps

JSON serialisation extensions now support BSON timestamps.

Contributed by Tom McMillen.

### Add allow-disk-use and Cursor Options to Aggregates

`monger.collection/aggregate` now supports `:cursor` and `:allow-disk-use` options.

Contributed by Bartek Marcinowski.


### monger.collection/ensure-index No Longer Shadows clojure.core/name

5-arity of `monger.collection/ensure-index` no longer shadows `clojure.core/name`
and fails with an obscure exception.

Contributed by Joshua Karstendick.


## Change Log

[Monger change log](https://github.com/michaelklishin/monger/blob/master/ChangeLog.md) is available on GitHub.



## Monger is a ClojureWerkz Project

[Monger](http://clojuremongodb.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client built around CQL
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Monger, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


## About the Author

[@michaelklishin](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
