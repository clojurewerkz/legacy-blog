---
layout: post
title: "Pantomime 2.3.0 is Released"
date: 2014-07-18 01:40:30 +0400
comments: false
categories:
  - pantomime
  - releases
---

## TL;DR

[Pantomime](http://github.com/michaelklishin/pantomime) is a tiny Clojure library for working with
MIME types and file metadata.


## Changes between Pantomime 2.2.0 and 2.3.0

### Extension Detection From MIME Type

`pantomime.mime/extension-for-name` is a new function that suggests
common extensions for MIME type names:

``` clojure
(require '[pantomime.mime :as pm])

(pm/extension-for-name "application/vnd.ms-excel")
;= ".xls"
(pm/extension-for-name "image/jpeg")
;= ".jpg"
(pm/extension-for-name "application/octet-stream")
;= ".bin"
```


## Changes between Pantomime 2.1.0 and 2.2.0

## Clojure 1.6

The library now depends on Clojure 1.6.


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
