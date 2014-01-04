---
layout: post
title: "Validateur 1.6.0 is released"
date: 2014-01-04 16:56
comments: false
categories:
  - validateur
  - releases
---

## TL;DR

[Validateur](http://clojurevalidations.info) is a functional validations library inspired by Ruby's ActiveModel.
Validateur 1.6 contains a usability improvement and drops Clojure 1.3 support.


## Changes between Validateur 1.5.0 and 1.6.0

### Corrected logic in blank/nil validations

Corrected the logic in the allowed-to-be-blank functions to properly allow nil values
when allow-nil is true, but allow-blank is false. Previously, both allow-blank and allow-nil
had to be set to true to allow nil values due to clojure's blank? function returning true for nil.

Contributed by Wes Johnson.

### Clojure 1.3 No Longer Supported

Clojure 1.3 is no longer supported by Validateur.


## Change Log

We recommend all users to upgrade to [1.6.0](https://clojars.org/com.novemberain/validateur/versions/1.6.0).

[Validateur change log](https://github.com/michaelklishin/validateur/blob/master/ChangeLog.md) is available on GitHub.


## Thank You, Contributors

Wes Johnson contributed key improvements in this release.



## Validateur is a ClojureWerkz Project

[Validateur](http://github.com/michaelklishin/validateur) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client built around CQL
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Validateur, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).

## About The Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
