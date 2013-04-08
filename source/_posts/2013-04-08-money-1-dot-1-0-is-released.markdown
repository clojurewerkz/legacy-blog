---
layout: post
title: "Money 1.1.0 is released"
date: 2013-04-08 22:06
comments: false
categories:
  - money
  - releases
---

[Money](https://github.com/clojurewerkz/money) is a Clojure library that deals with monetary amounts
and currencies, built on top of [Joda Money](http://joda-money.sourceforge.net/).

`1.1.0` is a minor release that contains **one breaking API change**, contains
minor improvements and upgrades dependencies.



## Changes between Money 1.0.0 and 1.1.0

### Comparison Functions

It is possible to compare monetary amounts using >, >=, < and <=.

```clojure
(require '[clojurewerkz.money.amounts    :as ma])
(require '[clojurewerkz.money.currencies :as mc])

(ma/< (ma/amount-of mc/USD 100) (ma/amount-of mc/USD 100))
;= false

(ma/<= (ma/amount-of mc/USD 100) (ma/amount-of mc/USD 100) (ma/amount-of mc/USD 120))
;= true

(ma/>= (ma/amount-of mc/USD 100) (ma/amount-of mc/USD 100) (ma/amount-of mc/USD 120))
;= false

(ma/> (ma/amount-of mc/USD 200) (ma/amount-of mc/USD 100))
;= true
```

Contributed by Ben Poweski.


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

and several others. If you like Quartzite, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).




[@michaelklishin](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
