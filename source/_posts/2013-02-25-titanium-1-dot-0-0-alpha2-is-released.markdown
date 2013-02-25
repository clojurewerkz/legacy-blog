---
layout: post
title: "Titanium 1.0.0-alpha2 is released"
date: 2013-02-25 23:03
comments: false
categories:
  - titanium
  - releases
---

## TL;DR

[Titanium](http://titanium.clojurewerkz.org) is a powerful Clojure graph library that is built on top of [Aurelius Titan](http://thinkaurelius.github.com/titan/).
It combines a Clojure-friendly API and graph processing DSL with the power of Titan.

`alpha2` is a development release that adds transaction control operations.


## Changes between Titanium 1.0.0-alpha1 and 1.0.0-alpha2

### Transaction Control Functions

`clojurewerkz.titanium.graph/commit-tx!` and `clojurewerkz.titanium.graph/rollback-tx!`
commit and roll back current transaction, respectively. Note that closing a
graph will automatically commit current transaction. Every operation
that modifies the graph will automatically start a transaction if needed.


### clojurewerkz.titanium.graph/get-vertices Now Accepts Keywords For Keys

`clojurewerkz.titanium.graph/get-vertices` now accepts keywords for keys,
like many other functions in Titanium.


## Change Log

[Titanium change log](https://github.com/clojurewerkz/titanium/blob/master/ChangeLog.md) is available on GitHub.


## News and Updates

New releases and updates are announced [on
Twitter](http://twitter.com/clojurewerkz). Titanium also has [a
mailing list](https://groups.google.com/group/clojure-titanium), feel
free to ask questions and report issues there.


## Titanium is a ClojureWerkz Project

Titanium is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Neocons](http://clojureneo4j.info), a Clojure client for the Neo4J REST API
 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Titanium, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz Team](http://twitter.com/clojurewerkz).
