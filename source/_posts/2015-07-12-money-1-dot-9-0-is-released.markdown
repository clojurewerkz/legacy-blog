---
layout: post
title: "Money 1.9.0 is released"
date: 2015-07-12 00:17:19 +0300
comments: false
categories:
  - money
  - releases
---

[Money](https://github.com/clojurewerkz/money) is a Clojure library that deals with monetary amounts
and currencies, built on top of [Joda Money](http://joda-money.sourceforge.net/).

`1.9.0` is a minor release.


## Changes Between 1.8.0 and 1.9.0

### New Amount Functions

`clojurewerkz.money.amounts/major-of`, `clojurewerkz.money.amounts/minor-of`,
and `clojurewerkz.money.amounts/currency-of` return major units (e.g. dollars,
minor units (e.g. cents), and currency unit from a provided monetary amount
(`Money` instance).

### Clojure 1.7 By Default

The project now depends on `org.clojure/clojure` version `1.7.0`. It is
still compatible with Clojure 1.6 and if your `project.clj` depends on
a different version, it will be used, but 1.7 is the default now.

We encourage all users to upgrade to 1.7, it is a drop-in replacement
for the majority of projects out there.



## Change Log

[Money change log](https://github.com/clojurewerkz/money/blob/master/ChangeLog.md) is available on GitHub.



## Money is a ClojureWerkz Project

[Money](https://github.com/clojurewerkz/money) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Cassaforte](http://clojurecassandra.info), a Clojure client for Cassandra built around CQL 3 
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB driver for a more civilized age
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Meltdown](http://github.com/clojurewerkz/meltdown), a Clojure interface to [Reactor](http://projectreactor.io/)

and several others. If you like Money, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).




[@michaelklishin](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
