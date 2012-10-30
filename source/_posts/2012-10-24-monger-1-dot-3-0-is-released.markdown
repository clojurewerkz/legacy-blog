---
layout: post
title: "Monger 1.3.0 is released"
date: 2012-10-24 12:10
comments: false
categories: 
  - releases
  - monger
---

## TL;DR

Monger is an idiomatic [Clojure MongoDB driver](http://clojuremongodb.info) for a more civilized age.
It has batteries included, offers powerful expressive query DSL, strives to support every MongoDB 2.0+ feature and has sane defaults.
It also has [solid documentation](http://clojuremongodb.info).

`1.3.0` is a minor *100% backwards-compatible* release that includes an important bug fix in the updated MongoDB Java driver.
We recommend all users to upgrade to it as soon as possible.


## Changes in 1.3.0

### monger.core/disconnect!

`monger.core/disconnect!` closes the default database connection.


### Ragtime 0.3.0

Ragtime dependency has been updated to 0.3.0.


### MongoDB Java Driver Update

MongoDB Java driver dependency has been [updated to 2.9.2](https://jira.mongodb.org/secure/ReleaseNote.jspa?projectId=10006&version=11891). This
includes *an important concurrency bug fix*: [JAVA-660](https://jira.mongodb.org/browse/JAVA-660).


### Cheshire Support

`monger.json` and `monger.joda-time` will now use [Cheshire](https://github.com/dakrone/cheshire) if it is available.
[clojure.data.json](https://github.com/clojure/data.json) is no longer a hard dependency (but `0.1.x` versions are still supported if available).

Recently released `clojure.data.json` version `0.2.0` completely breaks public API and is not supported. We recommend
all users prefer Cheshire when possible.


### ClojureWerkz Support 0.7.0

ClojureWerkz Support library is upgraded to `0.7`.


## Change Log

We recommend all users to upgrade to [1.3.0](https://clojars.org/com.novemberain/monger/versions/1.3.0) as soon as possible.

[Monger change log](https://github.com/michaelklishin/monger/blob/master/ChangeLog.md) is available on GitHub.



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
