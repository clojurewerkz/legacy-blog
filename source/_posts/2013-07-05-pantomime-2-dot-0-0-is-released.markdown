---
layout: post
title: "Pantomime 2.0.0 is released"
date: 2013-07-05 00:12
comments: false
categories:
  - pantomime
  - releases
---

## TL;DR

[Pantomime](http://github.com/michaelklishin/pantomime) is a tiny Clojure library for working with
MIME types and file metadata.

Pantomime 2.0 introduces a new (natural) language detection feature built on top of
Apache Tika and *drops support for Clojure 1.3*.

Future versions will likely introduce more functionality built on top of Tika, making
Pantomime more than just a "tiny libarry for working with MIME types").


## Changes between Pantomime 1.8.0 and 2.0.0

### Clojure 1.3 is No Longer Supported

Pantomime `2.0` drops support for Clojure 1.3.

### Language Detection Support

`pantomime.languages` is a new namespace that provides functions for
detecting natural languages:

``` clojure
(require '[pantomime.languages :as pl])

(pl/detect-language "this is English, it should not be hard to detect")
;= "en"

(pl/detect-language "parlez-vous Français")
;= "fr"
```


## Change Log

We recommend all users to upgrade to [2.0.0](https://clojars.org/com.novemberain/pantomime/versions/2.0.0).

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
