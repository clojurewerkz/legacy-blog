---
layout: post
title: "Monger 1.3.4 is released"
date: 2012-11-09 02:00
comments: false
categories: 
  - releases
  - monger
---

## TL;DR

Monger is an idiomatic [Clojure MongoDB driver](http://clojuremongodb.info) for a more civilized age.
It has batteries included, offers powerful expressive query DSL, strives to support every MongoDB 2.0+ feature and has sane defaults.
It also has [solid documentation](http://clojuremongodb.info).

`1.3.4` is a minor *100% backwards-compatible* release that eliminates more `data.json` dependencies in `monger.json`.
We recommend all users to upgrade to it as soon as possible.


## Changes between 1.3.3 and 1.3.4

### data.json Dependency Fixes

`monger.json` no longer requires `data.json` to be present at compile time.



## Change Log

We recommend all users to upgrade to [1.3.4](https://clojars.org/com.novemberain/monger/versions/1.3.4) as soon as possible.

[Monger change log](https://github.com/michaelklishin/monger/blob/1.3.x-stable/ChangeLog.md) is available on GitHub.



## Monger is a ClojureWerkz Project

[Monger](http://clojuremongodb.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Welle](https://clojureriak.info), a Riak client with batteries included
 * [Elastisch](https://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Neocons](https://clojureneo4j.info), a client for the Neo4J REST API
 * [Langohr](https://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Quartzite](https://clojurequartz.info), a powerful scheduling library

and several others. If you like Monger, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[@michaelklishin](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
