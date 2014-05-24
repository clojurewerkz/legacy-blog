---
layout: post
title: "Langohr 2.11.0 is released"
date: 2014-05-24 17:52:53 +0400
comments: false
categories:
  - langohr
  - releases
---

## TL;DR

Langohr is a small [Clojure RabbitMQ client](http://clojurerabbitmq.info).

`2.11.0` is a minor feature release.


## Changes between Langohr 2.10.x and 2.11.0

### Multi-Host Support In langohr.core/connect

`langohr.core/connect` now supports `:hosts` as well as `:host`.
The hosts provided will be iterated over, the first reachable host
will be used.

Example:

``` clojure
(require '[langohr.core :as rmq])

(rmq/connect {:hosts #{"192.168.1.2" "192.168.1.3"}})
;; uses port 5688 for both hosts
(rmq/connect {:hosts #{"192.168.1.2" "192.168.1.3"} :port 5688})
;; uses multiple host/port pairs
(rmq/connect {:hosts #{["192.168.1.2" 5688] ["192.168.1.3" 5689]}})
```


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
