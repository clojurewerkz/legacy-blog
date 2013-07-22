---
layout: post
title: "Cassaforte 1.1.0 is released"
date: 2013-07-22 21:41
comments: false
categories:
  - cassaforte
  - releases
---
## TL;DR

[Cassaforte](http://clojurecassandra.info) is a new Clojure client for
Apache Cassandra 1.2+.  It is built around CQL 3 and focuses on ease
of use. You will likely find that using Cassandra from Clojure has
never been so easy.

`1.1.0` is a minor release that introduces one bug fix and one minor
improvement.


## Changes between Cassaforte 1.0.1 and 1.1.0

### Fixes for prepared queries with multi-cql

Multi-cql didn't work with unforced prepared statements, now it's possible to use
`client/prepared` with multi-cql as well.

### Fixes for compound keys in iterate-world queries

Iterate world didn't work fro tables with compound primary keys. Now it's possible
to iterate over collections that have compound keys.

[Cassaforte change log](https://github.com/clojurewerkz/cassaforte/blob/master/ChangeLog.md) can be found on GitHub.


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
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Neocons](http://clojureneo4j.info), a Clojure client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Cassaforte, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz Team](http://twitter.com/clojurewerkz).
