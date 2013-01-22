---
layout: post
title: "Pantomime 1.5.0 is released"
date: 2013-01-23 01:03
comments: false
categories:
  - releases
  - pantomime
---

## TL;DR

[Pantomime](http://github.com/michaelklishin/pantomime) is a tiny Clojure library that deals with MIME types (Internet media types, "content types").
Pantomime 1.5 upgrades [Apache Tika to 1.3](http://www.apache.org/dist/tika/CHANGES-1.3.txt) and default Clojure dependency to 1.4.0.


## Changes between Pantomime 1.4.0 and 1.5.0

### Apache Tika 1.3

Apache Tika dependency has been upgraded to [version 1.3](http://www.apache.org/dist/tika/CHANGES-1.3.txt).

### Clojure 1.4 By Default

Pantomime now depends on `org.clojure/clojure` version `1.4.0`. It is still compatible with Clojure 1.3 and if your `project.clj` depends
on 1.3, it will be used, but 1.4 is the default now.

We encourage all users to upgrade to 1.4, it is a drop-in replacement for the majority of projects out there.


## Change Log

We recommend all users to upgrade to [1.5.0](https://clojars.org/com.novemberain/pantomime/versions/1.5.0).

[Pantomime change log](https://github.com/michaelklishin/pantomime/blob/master/ChangeLog.md) is available on GitHub.



## Pantomime is a ClojureWerkz Project

[Pantomime](http://github.com/michaelklishin/pantomime) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Monger](https://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Welle](https://clojureriak.info), a Riak client with batteries included
 * [Elastisch](https://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Neocons](https://clojureneo4j.info), a client for the Neo4J REST API
 * [Langohr](https://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Quartzite](https://clojurequartz.info), a powerful scheduling library

and several others. If you like Monger, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
