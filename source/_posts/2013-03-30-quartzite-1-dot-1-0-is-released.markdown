---
layout: post
title: "Quartzite 1.1.0 is released"
date: 2013-03-30 00:49
comments: false
categories: 
  - quartzite
  - releases
---

[Quartzite](http://clojurequartz.info) is a Clojure DSL on top of the Quartz scheduler.

`1.1.0` is a minor release that contains **one breaking API change**, contains
minor improvements and upgrades dependencies.



## Changes between Quartzite 1.0.0 and 1.1.0

`1.1.x` has one **breaking API change** in how it converts job context
maps to `JobDetailContext` in Quartz.

### clj-time upgraded to 0.5.0

[clj-time](https://github.com/seancorfield/clj-time) dependency has been upgraded to version 0.5.0, uses
[Joda Time 2.2](https://github.com/JodaOrg/joda-time/blob/master/RELEASE-NOTES.txt).

`clojurewerkz.quartzite.date-time` functions were pushed upstream to `clj-time`, find them in
`clj-time.core` and `clj-time.periodic`.

`clojurewerkz.quartzite.date-time` will be **removed** from Quartzite in the release following
`1.1.0`.

### Stringified Keys in JobDetailContext

Quartzite will now stringify all keys in Clojure maps converted to job detail context
instances. This is due to the fact that some Quartz internals implicitly assume JobDetailContext
keys are always strings. 


### Clojure 1.5 By Default

Quartzite now depends on `org.clojure/clojure` version `1.5.1`. It is
still compatible with Clojure 1.3+ and if your `project.clj` depends on
a different version, it will be used, but 1.5 is the default now.

We encourage all users to upgrade to 1.5, it is a drop-in replacement
for the majority of projects out there.



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
