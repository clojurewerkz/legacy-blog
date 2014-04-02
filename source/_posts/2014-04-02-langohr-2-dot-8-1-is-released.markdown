---
layout: post
title: "Langohr 2.8.1 is released"
date: 2014-04-02 23:00:54 +0400
comments: false
categories:
  - langohr
  - releases
---

## TL;DR

Langohr is a small [Clojure RabbitMQ client](http://clojurerabbitmq.info).

`2.8.1` is a minor feature release.


## Changes between Langohr 2.7.x and 2.8.1

### Client-side Channel Flow Removed

`langohr.channel/flow` and `langohr.channel/flow?` were removed.
Client-side flow control has been deprecated for a while and was removed
in RabbitMQ Java client 3.3.0.

### RabbitMQ Java Client Upgrade

RabbitMQ Java client dependency has been updated to `3.3.0`.

### Clojure 1.6 By Default

Langohr now depends on `org.clojure/clojure` version `1.6.0`. It is
still compatible with Clojure 1.4 and if your `project.clj` depends on
a different version, it will be used, but 1.6 is the default now.

We encourage all users to upgrade to 1.6, it is a drop-in replacement
for the majority of projects out there.

### langohr.http/protocol-ports

`langohr.http/protocol-ports` is a new function that returns
a map of protocol names to protocol ports. The protocols
are listed with `langohr.http/list-enabled-protocols`.



## Change Log

[Langohr change
log](https://github.com/michaelklishin/langohr/blob/master/ChangeLog.md)
is available on GitHub.


## Langohr is a ClojureWerkz Project

[Langohr](http://clojurerabbitmq.info) is part of the [group of
libraries known as ClojureWerkz](http://clojurewerkz.org), together
with

 * [Elastisch](http://clojureelasticsearch.info), a minimalistic well documented Clojure client for ElasticSearch
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client built around CQL 3.0
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Langohr, you may also like [our other
projects](http://clojurewerkz.org).

Let us know what you think [on
Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing
list](https://groups.google.com/group/clojure).

## About The Author

[Michael](http://twitter.com/michaelklishin) on behalf of the
[ClojureWerkz](http://clojurewerkz.org) Team
