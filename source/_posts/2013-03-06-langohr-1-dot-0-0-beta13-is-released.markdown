---
layout: post
title: "Langohr 1.0.0-beta13 is released"
date: 2013-03-06 21:10
comments: false
categories:
  - langohr
  - releases
---

## TL;DR

Langohr is a [Clojure RabbitMQ client](http://clojurerabbitmq.info) that embraces [AMQP 0.9.1 Model](http://www.rabbitmq.com/tutorials/amqp-concepts.html).

`1.0.0-beta13` is a development milestone release that *has breaking API changes*. While the previous API version will work for a while
for backwards compatibility, we recommend all users to upgrade to the new one early.


## Changes between Langohr 1.0.0-beta12 and 1.0.0-beta13

`1.0.0-beta13` has **BREAKING CHANGES**:

### langohr.consumers/subscribe Options Renamed

The options `langohr.consumers/subscribe` takes now have consistent naming:

 * `:handle-consume-ok` becomes `:handle-consume-ok-fn`
 * `:handle-cancel` becomes `:handle-cancel-fn`
 * `:handle-cancel-ok` becomes `:handle-cancel-ok-fn`
 * `:handle-shutdown-signal-ok` becomes `:handle-shutdown-signal-ok-fn`
 * `:handle-recover-ok` becomes `:handle-recover-ok-fn`
 * `:handle-delivery-fn` does not change

This makes handler argument names consistent across the board.

Previous options (`:handle-cancel`, etc) are still supported
for backwards compatibility but will eventually be removed.



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
