---
layout: post
title: "Meltdown 1.0.0-beta12 is released"
date: 2014-04-28 23:51:21 +0400
comments: false
categories:
  - releases
  - meltdown
---

## TL;DR

Meltdown is a Clojure interface to [Reactor](https://github.com/reactor), an asynchronous
programming, event passing and stream processing [toolkit for the JVM](http://spring.io/blog/2013/11/12/it-can-t-just-be-big-data-it-has-to-be-fast-data-reactor-1-0-goes-ga).

`1.0.0-beta12` is a development milestone with minor improvements, and likely
the last pre-release version before 1.0.



## Changes between 1.0.0-beta11 and 1.0.0-beta12

### Reactor Update

Reactor is updated to `1.1.0.RC1`.


## Changes between 1.0.0-beta10 and 1.0.0-beta11

### Set Membereship Selector

`clojurewerkz.meltdown.selectors/set-membership` is a new selector
that matches on element membership in a set:

``` clojure
(require '[clojurewerkz.meltdown.reactor   :as mr])
(require '[clojurewerkz.meltdown.selectors :as ms)

(let [r   (mr/create)]
  (mr/on r (ms/set-membership #{"white" "red" "blue"} (fn [evt])))
```



## Change log

[Meltodwn change log](https://github.com/clojurewerkz/meltdown/blob/master/ChangeLog.md) is available on GitHub.


## Meltdown is a ClojureWerkz Project

[Meltdown](https://github.com/clojurewerkz/meltdown) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a Clojure client for ElasticSearch
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client
 * [Titanium](http://titanium.clojurewerkz.org), a Clojure graph library
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Meltdown, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
