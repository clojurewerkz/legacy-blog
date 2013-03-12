---
layout: post
title: "Pantomime 1.7.0 is released"
date: 2013-03-12 23:48
comments: false
categories:
  - releases
  - pantomime
---

## TL;DR

[Pantomime](http://github.com/michaelklishin/pantomime) is a tiny Clojure library that deals with MIME types (Internet media types, "content types").
Pantomime 1.7 upgrades default Clojure dependency to 1.5.


## Changes between Pantomime 1.5.0 and 1.7.0

### Clojure 1.5 By Default

Pantomime now depends on `org.clojure/clojure` version `1.5.1`. It is still compatible with Clojure 1.3+ and if your `project.clj` depends
on a different version, it will be used, but 1.5 is the default now.

We encourage all users to upgrade to 1.5, it is a drop-in replacement for the majority of projects out there.


## Change Log

We recommend all users to upgrade to [1.7.0](https://clojars.org/com.novemberain/pantomime/versions/1.7.0).

[Pantomime change log](https://github.com/michaelklishin/pantomime/blob/master/ChangeLog.md) is available on GitHub.



## Pantomime is a ClojureWerkz Project

[Pantomime](http://github.com/michaelklishin/pantomime) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Pantomime, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
