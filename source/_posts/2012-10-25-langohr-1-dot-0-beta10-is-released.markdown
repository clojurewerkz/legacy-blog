---
layout: post
title: "Langohr 1.0-beta10 is released"
date: 2012-10-25 22:19
comments: false
categories:
  - releases
  - langohr
---

## TL;DR

Langohr is a [Clojure RabbitMQ client](http://clojurerabbitmq.info) that embraces [AMQP 0.9.1 Model](http://bitly.com/amqp-model-explained).

`1.0-beta10` is a development release with one fix release. We recommend all users to upgrade to it.


## Changes in 1.0-beta10

### langohr.basic/reject now correctly uses basic.reject

langohr.basic/reject now correctly uses `basic.reject` AMQP method
and not `basic.ack`.

Contributed by @natedev.



## Change Log

[Langohr change log](https://github.com/michaelklishin/langohr/blob/master/ChangeLog.md) is available on GitHub.


## Thank You, Contributors

* [natedev](http://github.com/natedev)


## Langohr is a ClojureWerkz Project

[Langohr](http://clojurerabbitmq.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic well documented Clojure client for ElasticSearch
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Langohr, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


The [ClojureWerkz](http://clojurewerkz.org) Team
