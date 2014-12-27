---
layout: post
title: "Quartzite 2.0 is released"
date: 2014-12-27 20:39:28 +0300
comments: false
categories:
  - quartzite
  - releases
---

[Quartzite](http://clojurequartz.info) is a Clojure DSL on top of the Quartz scheduler.

`2.0.0` is a major release that contains [breaking public API changes](http://blog.clojurewerkz.org/blog/2014/04/26/major-breaking-public-api-changes-coming-in-our-projects/).


## Changes Between Quartzite 1.3.0 and 2.0.0

### Scheduler as Explicit Arguments

Following our [commitment to make our projects rely less on dynamic vars](http://blog.clojurewerkz.org/blog/2014/04/26/major-breaking-public-api-changes-coming-in-our-projects/) we
have changed `clojurewerkz.quartzite.scheduler` function to take an explicit
scheduler argument.

So, in 1.3 releases, you would do:

``` clojure
(require '[clojurewerkz.quartzite.scheduler :as qs])

(qs/initialize)
(qs/start)
(qs/schedule job-detail trigger)
(qs/shutdown)
```

and in 2.0 release, the same code would look like so:

``` clojure
(require '[clojurewerkz.quartzite.scheduler :as qs])

(let [s (-> (qs/initialize) qs/start)]
  (qs/schedule s job-detail trigger)
  (qs/shutdown s))
```

### quartzite.date-time is Gone

`clojurewerkz.quartzite.date-time` was removed as all of the functions in that
namespace have been contributed to `clj-time` a while ago, and some provide more
correct or extensible functionality.

Simply use `clj-time` counterparts when upgrading.

### Clojure 1.4 and 1.5 are No Longer Supported

The library no longer supports Clojure 1.4 and 1.5 as of this version.



## Change Log

[Quartzite change log](https://github.com/michaelklishin/quartzite/blob/master/ChangeLog.md) is available on GitHub.



## Quartzite is a ClojureWerkz Project

[Quartzite](http://clojurequartz.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB driver for a more civilized age
 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API

and several others. If you like Quartzite, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).




[@michaelklishin](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
