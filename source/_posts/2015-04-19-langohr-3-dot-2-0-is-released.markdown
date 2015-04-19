---
layout: post
title: "Langohr 3.2.0 is released"
date: 2015-04-19 03:05:39 +0300
comments: false
categories:
  - langohr
  - rabbitmq  
  - releases
---

## TL;DR

Langohr is a small [Clojure RabbitMQ client](http://clojurerabbitmq.info).

`3.2.0` is a minor feature release.


## Changes between Langohr 3.1.x and 3.2.0

### Authentication Mechanism Support

Langohr now converts `:authentication-mechanism` option to a SASL
mechanism. Two values are supported:

 * `"PLAIN"`
 * `"EXTERNAL"`

Contributed by Tap.

### RabbitMQ Java Client Upgrade

RabbitMQ Java client dependency has been updated to `3.5.x`.



## Change Log

[Langohr change log](https://github.com/michaelklishin/langohr/blob/master/ChangeLog.md)
is available on GitHub.


## Langohr is a ClojureWerkz Project

[Langohr](http://clojurerabbitmq.info) is part of the [group of
libraries known as ClojureWerkz](http://clojurewerkz.org), together
with

 * [Elastisch](http://clojureelasticsearch.info), a minimalistic well documented Clojure client for ElasticSearch
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client built around CQL 3.0
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Langohr, you may also like [our other
projects](http://clojurewerkz.org).

Let us know what you think [on
Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing
list](https://groups.google.com/group/clojure).

## About The Author

[Michael](http://twitter.com/michaelklishin) on behalf of the
[ClojureWerkz](http://clojurewerkz.org) Team
