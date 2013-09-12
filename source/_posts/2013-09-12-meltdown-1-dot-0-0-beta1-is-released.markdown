---
layout: post
title: "Meltdown 1.0.0-beta1 is Released"
date: 2013-09-12 19:45
comments: false
categories:
  - meltdown
  - releases
---

## TL;DR

Meltdown is a Clojure interface to [Reactor](https://github.com/reactor), an asynchronous
programming, event passing and stream processing toolkit for the JVM.

`1.0.0-beta1` is a development milestone release that introduces one feature
and updates [Reactor](https://github.com/reactor/reactor) to `1.0.0.M3`.



## Changes between 1.0.0-alpha3 and 1.0.0-beta1

### Reactor Update

Reactor is updated to `1.0.0.M3`.


### Added dispatcher option to reactor and stream composition

When creating reactor, it's now possible to plug in a custom dispatcher or configure an underlying
dispatcher in a way that's most suitable for your application, for example:

```clj
(ns my-app.core
  (:import [reactor.event.dispatch RingBufferDispatcher]
           [com.lmax.disruptor.dsl ProducerType]
           [com.lmax.disruptor YieldingWaitStrategy]))

;; Creates a RingBuffer Dispatcher, with a custom queue size of 4096
(def reactor (mr/create :dispatcher (RingBufferDispatcher. "dispatcher-name"
                                                            4096
                                                            ProducerType/MULTI
                                                            (YieldingWaitStrategy.))))
```




## Change log

[Meltodwn change log](https://github.com/clojurewerkz/meltdown/blob/master/ChangeLog.md) is available on GitHub.


## Meltdown is a ClojureWerkz Project

[Meltdown](https://github.com/clojurewerkz/meltdown) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a Clojure client for ElasticSearch
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client
 * [Titanium](http://titanium.clojurewerkz.org), a Clojure graph library
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Elastisch, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
