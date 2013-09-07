---
layout: post
title: "Cassaforte 1.2.0 is released"
date: 2013-09-07 23:03
comments: false
categories:
  - releases
  - cassaforte
---

## TL;DR

[Cassaforte](http://clojurecassandra.info) is a new Clojure client for
Apache Cassandra 1.2+.  It is built around CQL 3 and focuses on ease
of use. You will likely find that using Cassandra from Clojure has
never been so easy.

`1.2.0` is a minor release that introduces one minor feature, fixes a
couple of bugs, and makes Cassaforte compatible with Cassandra 2.0.


## Changes between Cassaforte 1.1.x and 1.2.0

### Cassandra Java Driver Update

Cassandra Java driver has been updated to `1.0.3` which should
support Cassandra 2.0.

### Fix problem with batched prepared statements

`insert-batch` didn't play well with prepared statements, problem fixed now. You can use `insert-batch`
normally with prepared statements.

### Hayt query generator update

Hayt is updated to 1.1.3 version, which contains fixes for token function and some internal improvements
that do not influence any APIs.

### Added new Consistency level DSL

Consistency level can now be (also) passed as a symbol, without resolving it to ConsistencyLevel instance:

```clojure
(client/with-consistency-level :quorum
       (insert :users r))
```

Please note that old DSL still works and is supported.

### Password authentication supported

Password authentication is now supported via the `:credentials` option to `client/build-cluster`.
Give it a map with username and password:

```clojure
(client/build-cluster {:contact-points ["127.0.0.1"]
                       :credentials {:username "ceilingcat" :password "ohai"}
                       ;; ...
```

Query DSL added for managing users `create-user`, `alter-user`, `drop-user`, `grant`, `revoke`,
`list-users`, `list-permissions` for both multi and regular sessions.


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
