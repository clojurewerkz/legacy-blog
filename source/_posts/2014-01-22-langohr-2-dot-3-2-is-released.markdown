---
layout: post
title: "Langohr 2.3.2 is released"
date: 2014-01-22 17:06:27 +0400
comments: false
categories:
  - langohr
  - rabbitmq
  - releases
---

## TL;DR

Langohr is a small [Clojure RabbitMQ client](http://clojurerabbitmq.info).

`2.3.2` is a minor feature and bug fix release based on community feedback on connection
recovery.


## Changes between Langohr 2.2.1 and 2.3.2

### Deprecations

`langohr.core/automatically-recover?` is deprecated

Use `langohr.core/automatic-recovery-enabled?` instead.

### Recovery Predicates

`langohr.core/automatic-recovery-enabled?` and
`langohr.core/automatic-topology-recovery-enabled?` are new predicate
functions that return `true` if automatic connection and topology
recovery, respectively, is enabled for the provided connection.

### Topology Recovery Fails Quickly

Topology recovery now fails quickly, raising
`com.novemberain.langohr.recovery.TopologyRecoveryException` which
carries the original (cause) exception.

Previously if recovery of an entity failed, other entities were still
recovered. Now topology recovery fails on the first exception,
making issues more visible.

### Automatic Recovery Can Be Disabled By Passing `nil`

Automatic recovery options now respect both `false` and `nil` values.



## Change Log

[Langohr change
log](https://github.com/michaelklishin/langohr/blob/2.3.x-stable/ChangeLog.md)
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
