---
layout: post
title: "Cassaforte 1.3.0 is released"
date: 2014-05-15 22:17:44 +0400
comments: false
categories:
  - cassaforte
  - releases
---

## TL;DR

[Cassaforte](http://clojurecassandra.info) is a new Clojure client for
Apache Cassandra. It is built around CQL 3 and focuses on ease
of use. You will likely find that using Cassandra from Clojure has
never been so easy.

`1.3.0` is a minor release that introduces a few minor features and
improves compatibility with Cassandra 2.0.


## Changes between Cassaforte 1.2.x and 1.3.0

### Clojure 1.6 By Default

The project now depends on `org.clojure/clojure` version `1.6.0`. It is
still compatible with Clojure 1.4 and if your `project.clj` depends on
a different version, it will be used, but 1.6 is the default now.

We encourage all users to upgrade to 1.6, it is a drop-in replacement
for the majority of projects out there.


### Cassandra Java Driver Update

Cassandra Java driver has been updated to `2.0.x`.


### UUID Generation Helpers

`clojurewerkz.cassaforte.uuids` is a new namespace that provides UUID
generation helpers:

``` clojure
(require '[clojurewerkz.cassaforte.uuids :as uuids])

(uuids/random)
;= #uuid "d43fdc16-a9c3-4d0f-8809-512115289537"

(uuids/time-based)
;= #uuid "90cf6f40-4584-11e3-90c2-65c7571b1a52"

(uuids/unix-timestamp (uuids/time-based))
;= 1383592179743

(u/start-of (u/unix-timestamp (u/time-based)))
;= #uuid "ad1fd130-4584-11e3-8080-808080808080"

(u/end-of (u/unix-timestamp (u/time-based)))
;= #uuid "b31abb3f-4584-11e3-7f7f-7f7f7f7f7f7f"
```

### Hayt Update

Hayt dependency has been updated to `1.4.1`, which supports
`if-not-exists` in `create-keyspace`:

``` clojure
(create-keyspace "main"
	         (if-not-exists)
	         (with {:replication
	                  {:class "SimpleStrategy"
	                   :replication_factor 1 }}))
```

### Extra Clauses Support in `insert-batch`

It is now possible to use extra CQL clauses for every statement
in a batch insert (e.g. to specify TTL):

``` clojure
(cql/insert-batch "table"
  {:something "cats"}
  [{:something "dogs"} (using :ttl 60)])
```

Contributed by Sam Neubardt.

### Alternative `where` syntax

Now it is possible to specify hash in where clause, which makes queries 
more composable:

```clj
(select :users
        (where {:city "Munich"
                :age [> (int 5)]})
        (allow-filtering true))
```

### Batch Insert Improvements

Clauses to be specified for each record in `insert-batch`:

``` clojure
(let [input [[{:name "Alex" :city "Munich"} (using :ttl 350)]
             [{:name "Alex" :city "Munich"} (using :ttl 350)]]]
  (insert-batch th/session :users input))
```

Contributed by Sam Neubardt.



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
