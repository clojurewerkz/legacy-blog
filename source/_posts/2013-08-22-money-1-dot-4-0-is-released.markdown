---
layout: post
title: "Money 1.4.0 is released"
date: 2013-08-22 23:32
comments: true
categories:
  - money
  - releases
---

[Money](https://github.com/clojurewerkz/money) is a Clojure library that deals with monetary amounts
and currencies, built on top of [Joda Money](http://joda-money.sourceforge.net/).

`1.4.0` is a minor release that has no breaking API changes.



## Changes between Money 1.3.0 and 1.4.0

### Roudning Multiplication

`clojuremowerkz.money.amount/multiply` now provides another
arity that allows for multiplication by a double, just like
with `divide`:

``` clojure
(ams/multiply (ams/amount-of cu/USD 45) 10.1 :floor)
;= USD 454.50
```



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
