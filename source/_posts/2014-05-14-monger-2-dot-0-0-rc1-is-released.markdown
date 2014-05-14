---
layout: post
title: "Monger 2.0.0-rc1 is released"
date: 2014-05-14 07:25:00 +0400
comments: false
categories: 
  - monger
  - mongodb
  - releases
---

## TL;DR

Monger is an idiomatic [Clojure MongoDB driver](http://clojuremongodb.info) for a more civilized age.
It has batteries included, offers powerful expressive query DSL, strives to support every MongoDB 2.0+ feature and has sane defaults.
It also has [solid documentation](http://clojuremongodb.info).

`2.0.0` is a major *backwards-incompatible* release that implements in
Monger the [major breaking API
changes](http://blog.clojurewerkz.org/blog/2014/04/26/major-breaking-public-api-changes-coming-in-our-projects/)
announced earlier for several ClojureWerkz projects.


## Changes between 1.8.0 and 2.0.0

`2.0` is a major release that has **breaking public API changes**.

### Explicit Connection/DB/GridFS Argument

In Monger 2.0, all key public API functions require an explicit
DB/connection/GridFS object to be provided instead of relying on
a shared dynamic var. This makes Monger much easier to use with
systems such as Component and Jig, as well as concurrent
applications that need to work with multiple connections, database,
or GridFS filesystems.

In other words, instead of

``` clojure
(require '[monger.collection :as mc])

(mc/insert "libraries" {:name "Monger"})
```

it is now necessary to do

``` clojure
(require '[monger.collection :as mc])

(mc/insert db "libraries" {:name "Monger"})
```

This also means that `monger.core/connect!` and
`monger.core/connect-via-uri!` were removed, as was
`monger.multi` namespaces.

To connect to MongoDB, use `monger.core/connect`:

``` clojure
(require '[monger.core :as mg])

(let [conn (mg/connect)])
```

or `monger.core/connect-via-uri`:

``` clojure
(require '[monger.core :as mg])

(let [{:keys [conn db]} (mg/connect-via-uri "mongodb://clojurewerkz/monger:monger@127.0.0.1/monger-test4")])
```

To get a database reference, use `monger.core/get-db`, which now requires a connection
object:

``` clojure
(require '[monger.core :as mg])

(let [conn (mg/connect)
      db   (mg/get-db conn "monger-test")])
```

### Options as Maps

Functions that take options now require a proper Clojure map instead of
pseudo keyword arguments:

``` clojure
# in Monger 1.x
(mc/update db coll {} {:score 0} :multi true)

# in Monger 2.x
(mc/update db coll {} {:score 0} {:multi true})
```



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
