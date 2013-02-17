---
layout: post
title: "Langohr 1.0.0-beta11 is released"
date: 2013-02-17 14:10
comments: false
categories:
  - releases
  - langohr
---

## TL;DR

Langohr is a [Clojure RabbitMQ client](http://clojurerabbitmq.info) that embraces [AMQP 0.9.1 Model](http://www.rabbitmq.com/tutorials/amqp-concepts.html).

`1.0.0-beta11` is a development milestone release. We recommend all users to upgrade to it.


## Changes between Langohr 1.0.0-beta10 and 1.0.0-beta11

### HTTP API Client

Langohr `1.0.0-beta11` features initial bits of RabbitMQ HTTP API client
under `langohr.http`.


### More Convenient TLS Support

Langohr will now automatically enable TLS/SSL if provided `:port` is
`5671`.


### RabbitMQ Java Client 3.0.x

RabbitMQ Java Client has been upgraded to version `3.0.2`.


### langohr.exchange/declare-passive

`langohr.exchange/declare-passive` is a new function that performs passive
exchange declaration (checks if an exchange exists).

An example to demonstrate:

``` clojure
(require '[langohr.channel  :as lch])
(require '[langohr.exchange :as le])

(let [ch (lch/open conn)]
  (le/declare-passive ch "an.exchange"))
```

If the exchange does exist, the function works just like `langohr.exchange/declare`. If not,
an exception (`com.rabbitmq.client.ShutdownSignalException`, `java.io.IOException`) will be thrown.



## Change Log

[Langohr change log](https://github.com/michaelklishin/langohr/blob/master/ChangeLog.md) is available on GitHub.


## Langohr is a ClojureWerkz Project

[Langohr](http://clojurerabbitmq.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Elastisch](http://clojureelasticsearch.info), a minimalistic well documented Clojure client for ElasticSearch
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Langohr, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
