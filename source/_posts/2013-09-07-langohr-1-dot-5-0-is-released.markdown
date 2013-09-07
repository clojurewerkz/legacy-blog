---
layout: post
title: "Langohr 1.5.0 is released"
date: 2013-09-07 11:11
comments: false
categories:
  - langohr
  - releases
---

## TL;DR

Langohr is a [Clojure RabbitMQ client](http://clojurerabbitmq.info) that embraces [AMQP 0.9.1 Model](http://www.rabbitmq.com/tutorials/amqp-concepts.html).

`1.5.0` is a minor feature release.


## Changes between Langohr 1.4.0 and 1.5.0

### Automatic Recovery Improvements

Automatic recovery of channels that are created without an explicit
number now works correctly.

Contributed by Joe Freeman.


### clj-http Upgrade

clj-http dependency has been updated to `0.7.6`.


### Clojure 1.3 is No Longer Supported

Langohr requires Clojure 1.4+ as of this version.


### More Convenient Publisher Confirms Support

`langohr.confirm/wait-for-confirms` is a new function that
waits until all outstanding confirms for messages
published on the given channel arrive. It optionally
takes a timeout:

``` clojure
(langohr.confirm/wait-for-confirms ch)
;; wait up to 200 milliseconds
(langohr.confirm/wait-for-confirms ch 200)
```



## Change Log

[Langohr change log](https://github.com/michaelklishin/langohr/blob/1.5.x-stable/ChangeLog.md) is available on GitHub.


## Langohr is a ClojureWerkz Project

[Langohr](http://clojurerabbitmq.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Elastisch](http://clojureelasticsearch.info), a minimalistic well documented Clojure client for ElasticSearch
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client built around CQL 3.0
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Langohr, you may also like [our other
projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
