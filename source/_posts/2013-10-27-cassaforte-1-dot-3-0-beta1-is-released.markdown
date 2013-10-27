---
layout: post
title: "Cassaforte 1.3.0-beta1 is released"
date: 2013-10-27 05:09
comments: false
categories:
  - cassaforte
  - cassandra
  - releases
---

## TL;DR

[Cassaforte](http://clojurecassandra.info) is a Clojure client for
Apache Cassandra 1.2+. It is built around CQL 3 and focuses on ease
of use. You will likely find that using Cassandra from Clojure has
never been so easy.

`1.3.0-beta1` is a milestone release that introduces one minor feature
and upgrades Cassandra Java driver.


## Changes between Cassaforte 1.2.x and 1.3.0-beta1

### Extra Clauses Support in `insert-batch`

It is now possible to use extra CQL clauses for every statement
in a batch insert (e.g. to specify TTL):

``` clojure
(cql/insert-batch "table"
  {:something "cats"}
  [{:something "dogs"} (using :ttl 60)])
```

Contributed by Sam Neubardt.

### Cassandra Java Driver Update

Cassandra Java driver has been updated to `1.0.4` which
contains a [bunch of bug fixes](https://raw.github.com/datastax/java-driver/1.0/driver-core/CHANGELOG.rst).


## Thank You, Contributors

Kudos to Sam Neubardt for contributing to this release.


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


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz Team](http://twitter.com/clojurewerkz).
