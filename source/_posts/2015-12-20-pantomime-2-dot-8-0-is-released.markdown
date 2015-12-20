---
layout: post
title: "Pantomime 2.8.0 is released"
date: 2015-12-20 18:11:26 +0300
comments: false
categories:
  - pantomime
  - releases
---

## TL;DR

[Pantomime](http://github.com/michaelklishin/pantomime) is a Clojure interface to Apache Tika.
`2.8.0` is a minor release that upgrades Tika and introduces a minor feature.


## Changes between Pantomime 2.7.0 and 2.8.0

### Apache Tika 1.11

Apache Tika dependency has been upgraded to [version 1.11](http://www.apache.org/dist/tika/CHANGES-1.11.txt).

### MIME Pattern Extension

`pantomime.mime/add-pattern` is a new function that makes
it possible to extent MIME patterns used by the library:

``` clojure
(require '[pantomime.mime :as pm])

(pm/add-pattern "text/lorem-ipsum" ".+\\.ipsum$" "lorem.ipsum")
```

Contributed by Daniel Woelfel and Tommi Reinikainen.

## Clojure 1.7

The library now depends on Clojure 1.7.


## Change Log

[Pantomime change log](https://github.com/michaelklishin/pantomime/blob/master/ChangeLog.md) is available on GitHub.



## Pantomime is a ClojureWerkz Project

[Pantomime](http://github.com/michaelklishin/pantomime) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client built around CQL
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Pantomime, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
