---
layout: post
title: "Introducing ClojureWerkz Money"
date: 2013-04-02 01:27
comments: false
categories:
  - money
  - releases
---

## TL;DR

[ClojureWerkz Money](https://github.com/clojurewerkz/money) is a tiny Clojure library for working with money and currencies.
It is built on top of [Joda Money](http://joda-money.sourceforge.net/). Money is small, easy to use,
integrates with [Monger](http://clojuremongodb.info) and Cheshire.


## Money, Money, Money

Many ClojureWerkz projects take advantage of existing mature JVM libraries. Today we introduce another
library to this club: [Money](https://github.com/clojurewerkz/money). Money is a very thin layer on top of [Joda Money](http://joda-money.sourceforge.net), an excellent
money library from the creator of Joda Time.


## What's In The Box

 * Operations on monetary amounts (add, substract, multiply, divide, negate, etc)
 * Conversion between currencies
 * Support for multiple rounding modes
 * Parsing of strings (e.g. `USD 20`)
 * Currency unit looks by ISO-4217 code and country
 * [Cheshire](https://github.com/dakrone/cheshire) integration
 * [Monger](http://clojuremongodb.info) integration


## Documentation

Money is a small library and all of its [documentation guide fits in the README](https://github.com/clojurewerkz/money#documentation).



## Supported Clojure Versions

Money supports Clojure 1.4+.



## News and Updates

New releases and updates are announced [on Twitter](http://twitter.com/clojurewerkz).


## Money is a ClojureWerkz Project

Money is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Neocons](http://clojureneo4j.info), a Clojure client for the Neo4J REST API
 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Money, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz Team](http://twitter.com/clojurewerkz).
