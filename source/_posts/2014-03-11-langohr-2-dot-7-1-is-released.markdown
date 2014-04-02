---
layout: post
title: "Langohr 2.7.1 is released"
date: 2014-03-11 10:03:38 +0400
comments: false
categories:
  - langohr
  - rabbitmq
  - releases
---

## TL;DR

Langohr is a small [Clojure RabbitMQ client](http://clojurerabbitmq.info).

`2.7.1` is a minor feature release.


## Changes between Langohr 2.6.x and 2.7.1

### langohr.http/list-enabled-protocols

`langohr.http/list-enabled-protocols` is a new function that lists
the protocols a RabbitMQ installation supports, e.g. `"amqp"` or `"mqtt"`.
Note that this currently does not include WebSTOMP (due to certain technical decisions
in RabbitMQ Web STOMP plugin).


## Changes between Langohr 2.5.x and 2.6.0

### langohr.http/list-connections-from, /close-connections-from

`langohr.http/list-connections-from` and `langohr.http/close-connections-from`
are two new functions that list and close connections for a given username,
respectively:

``` clojure
(require '[langohr.http :as hc])

(hc/list-connections-from "guest")
;= a list of connections with username "guest"

;; closes all connections from "guest"
(hc/close-connections-from "guest")
```

### clj-http Upgrade

clj-http dependency has been updated to `0.9.0`.



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
