---
layout: post
title: "Quartzite 1.3.0 is released"
date: 2014-07-31 06:20:01 +0400
comments: false
categories:
  - quartzite
  - releases
---

[Quartzite](http://clojurequartz.info) is a Clojure DSL on top of the Quartz scheduler.

`1.3.0` is a minor release that contains
minor improvements and upgrades dependencies.


## Changes Between Quartzite 1.2.0 and 1.3.0

### Clojure 1.6 by Default

The library now depends on Clojure 1.6.

### clj-time upgraded to 0.8.0

[clj-time](https://github.com/clj-time/clj-time) dependency has been upgraded to version 0.8.0.


## Changes between Quartzite 1.1.0 and 1.2.0

### Clojure 1.3 is No Longer Supported

Quartzite requires Clojure 1.4+ as of this version.


### clj-time upgraded to 0.6.0

[clj-time](https://github.com/clj-time/clj-time) dependency has been upgraded to version 0.6.0.

### New Functions

* `clojurewerkz.quartzite.scheduler/get-currently-executing-jobs` returns a set of currently executing jobs.
* `clojurewerkz.quartzite.scheduler/currently-executing-job?` returns true there is a running job for a given key.



## Change Log

[Quartzite change log](https://github.com/michaelklishin/quartzite/blob/master/ChangeLog.md) is available on GitHub.



## Quartzite is a ClojureWerkz Project

[Quartzite](http://clojurequartz.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB driver for a more civilized age
 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API

and several others. If you like Quartzite, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).




[@michaelklishin](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
