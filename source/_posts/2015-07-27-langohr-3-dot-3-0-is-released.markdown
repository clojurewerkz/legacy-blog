---
layout: post
title: "Langohr 3.3.0 is released"
date: 2015-07-27 10:25:29 +0300
comments: false
categories:
  - langohr
  - rabbitmq
  - releases
---

## TL;DR

Langohr is a small [Clojure RabbitMQ client](http://clojurerabbitmq.info).

`3.3.0` is a minor feature release.


## Changes between Langohr 3.2.x and 3.3.0

### Forgiving Exception Handler by Default

Langohr now uses Java client's [forgiving exception handler](https://github.com/rabbitmq/rabbitmq-server/releases/tag/rabbitmq_v3_5_4)
by default. This means unhandled consumer exceptions
won't result in channel closure.


### RabbitMQ Java Client Upgrade

RabbitMQ Java client dependency has been updated to `3.5.4`.

### clj-http Upgrade

clj-http dependency has been updated to `2.0.0`.

This version of clj-http bumps Apache HTTP client version to 4.5.
If this is undesirable for your project, you can exclude Langohr's
dependency on clj-http and use another version.

See Langohr's `project.clj` (the `cljhttp076` profile).

### Cheshire Upgrade

Cheshire dependency has been updated to `5.5.0`.



## Change Log

[Langohr change log](https://github.com/michaelklishin/langohr/blob/master/ChangeLog.md)
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
