---
layout: post
title: "Money 1.3.0 is released"
date: 2013-04-24 20:37
comments: false
categories: 
  - money
  - releases
---

[Money](https://github.com/clojurewerkz/money) is a Clojure library that deals with monetary amounts
and currencies, built on top of [Joda Money](http://joda-money.sourceforge.net/).

`1.3.0` is a minor release that has no breaking API changes and several minor features.



## Changes between Money 1.2.0 and 1.3.0

### Hiccup Integration

`clojurewerkz.money.hiccup`, when compiled, will extend Hiccup's HTML
rendering protocol for monetary amounts and currency units. Internally
it uses default formatter used by `clojurewerkz.money.format`:
`clojurewerkz.money.format/*default-formatter*`, which can be rebound.

### Formatting of Monetary Amounts

`clojurewerkz.money.format/format` is a new function that formats
monetary amounts using default or provided locale:

``` clojure
(require '[clojurewerkz.money.currencies :as cu)
(require '[clojurewerkz.money.amounts :refer [amount-of])
(require '[clojurewerkz.money.format :refer :all])

(import java.util.Locale)

;; format using default system locale
(format (amount-of cu/GBP 20.0) Locale/UK) ;= GBP20,00
;; format using UK locale
(format (amount-of cu/GBP 20.0) Locale/UK) ;= £10.00
```

Custom Joda Money formatters are also supported.


### Addition and Subtraction of Monetary Amounts

`clojurewerkz.money.amounts/plus` and `clojurewerkz.money.amounts/minus` now accept
monetary amounts as well as doubles as 2nd argument.

Contributed by Ryan Neufeld.



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
