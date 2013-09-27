---
layout: post
title: "Monger 1.7.0-beta1 is released"
date: 2013-09-27 08:50
comments: false
categories:
  - monger
  - releases
---

## TL;DR

Monger is an idiomatic [Clojure MongoDB driver](http://clojuremongodb.info) for a more civilized age.
It has batteries included, offers powerful expressive query DSL, strives to support every MongoDB 2.0+ feature and has sane defaults.
It also has [solid documentation](http://clojuremongodb.info).

`1.7.0-beta1` is a *completely backwards-compatible* (besides dropped Clojure 1.3 support)
development milestone that introduces a few minor features and updated dependencies.


## Changes between 1.6.0 and 1.7.0-beta1

### Fune Tuning Cursor Options

`monger.query` DSL now provides a way to fine tune database cursor
options:

``` clojure
(with-collection "products"
  ...
  (options {:notimeout true, :slaveok false}) ;; where keyword matches Bytes/QUERYOPTION_*
  (options [:notimeout :slaveok])
  (options com.mongodb.Bytes/QUERYOPTION_NOTIMEOUT) ;; support Java constants
  (options :notimeout)
  ...
```

`monger.cursor` is a new namespace that provides the plumbing for cursor
fine tuning but should not be widely used directly.



### Joda Time Integration Improvements: LocalDate

`LocalDate` instance serialization is now supported
by Monger Joda Time integration.

Contributed by Timo Sulg.


### Clojure 1.3 Is No Longer Supported

Monger now officially supports Clojure 1.4+.


### Cheshire Upgrade

[Cheshire](https://github.com/dakrone/cheshire) dependency has been upgraded to 5.2.0


### ClojureWerkz Support Upgrade

ClojureWerkz Support dependency has been updated to `0.19.0`.


### Validateur 1.5.0

[Validateur](https://github.com/michaelklishin/validateur) dependency has been upgraded to 1.5.0.



## Change Log

[Monger change log](https://github.com/michaelklishin/monger/blob/master/ChangeLog.md) is available on GitHub.



## Thank You, Contributors

Timo Sulg contributed key features in this release.



## Monger is a ClojureWerkz Project

[Monger](http://clojuremongodb.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client built around CQL
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Monger, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[@michaelklishin](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
