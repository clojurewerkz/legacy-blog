---
layout: post
title: "Money 1.7.0 is released"
date: 2014-11-07 23:08:44 +0300
comments: false
categories:
  - money
  - releases
---

[Money](https://github.com/clojurewerkz/money) is a Clojure library that deals with monetary amounts
and currencies, built on top of [Joda Money](http://joda-money.sourceforge.net/).

`1.7.0` is a minor release.



## Changes between 1.6.0 and 1.7.0

### ZMK Currency Removed

In accordance with a Joda Money `0.10.0` change, ZMK is no longer
on the list of known currencies (use ZMW instead).

### Joda Money 0.10

Joda Money was upgraded to 0.10.0.



## Changes between 1.5.0 and 1.6.0

### Clojure 1.6 By Default

The project now depends on `org.clojure/clojure` version `1.6.0`. It is
still compatible with Clojure 1.4 and if your `project.clj` depends on
a different version, it will be used, but 1.6 is the default now.

We encourage all users to upgrade to 1.6, it is a drop-in replacement
for the majority of projects out there.


## Changes between 1.4.0 and 1.5.0

### Comparison Function Correctness

`<`, `>`, `<=`, `>=` now return a boolean on the 1-arg arity, as per docstring.

Contributed by Nicola Mometto.


## Change Log

[Money change log](https://github.com/clojurewerkz/money/blob/master/ChangeLog.md) is available on GitHub.



## Money is a ClojureWerkz Project

[Money](https://github.com/clojurewerkz/money) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB driver for a more civilized age
 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Money, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).




[@michaelklishin](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
