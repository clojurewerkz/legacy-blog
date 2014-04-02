---
layout: post
title: "Propertied 1.2.0 is released"
date: 2014-04-02 18:12:00 +0400
comments: false
categories:
  - propertied
  - releases
---

## TL;DR

[Propertied](http://https://github.com/michaelklishin/propertied) is a
tiny Clojure library for working with Java property lists
(java.util.Properties).


## Changes Between 1.1.0 and 1.2.0

### Keywords Support

`properties/map->properties` now supports keywords keys. `properties/properties->map` got a new
arity that converts keys to keywords:

``` clojure
(require '[clojurewerkz.propertied.properties :as p])

;; converts keys to keywords
(p/properties->map props true)
```

### Clojure 1.6 By Default

The project now depends on `org.clojure/clojure` version `1.6.0`. It is
still compatible with Clojure 1.4 and if your `project.clj` depends on
a different version, it will be used, but 1.6 is the default now.

We encourage all users to upgrade to 1.6, it is a drop-in replacement
for the majority of projects out there.


## Full Change Log

[Propertied change log](https://github.com/michaelklishin/propertied/blob/master/ChangeLog.md) is available on GitHub.



## Propertied is a ClojureWerkz Project

[Propertied](http://https://github.com/michaelklishin/propertied) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client built around CQL
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Propertied, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on
Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing
list](https://groups.google.com/group/clojure).

## About The Author

[Michael](http://twitter.com/michaelklishin) on behalf of the
[ClojureWerkz](http://clojurewerkz.org) Team
