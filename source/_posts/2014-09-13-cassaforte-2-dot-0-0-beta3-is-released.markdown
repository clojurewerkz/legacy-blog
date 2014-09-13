---
layout: post
title: "Cassaforte 2.0.0-beta3 is released"
date: 2014-09-13 23:14:37 +0400
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


## Changes between 2.0.0-beta2 and 2.0.0-beta3

### Cassandra 2.1 Compatibility

Cassaforte 2.0 is compatible with Cassandra 2.1.


### Prepared Statement Cache Removed

Prepared statement cache was affecting client correctness in some cases
and was removed.


### Clojure 1.7.0-alpha2+ Compatibility

Cassaforte is now compatible with Clojure `1.7.0-alpha2` and later versions.


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
