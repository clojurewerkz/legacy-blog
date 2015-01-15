---
layout: post
title: "EEP 1.0.0-beta1 is released"
date: 2015-01-15 23:09:21 +0300
comments: false
categories:
  - eep
  - releases
---

[EEP](http://blog.clojurewerkz.org/blog/2013/08/29/stream-processing-with-eep/) (Embeded Event Processing) is a Clojure stream processing library.

`1.0.0-beta1` is a development milestone that introduces
a **breaking public API** change and adapts to Meltdown `1.1.x` releases.


## Changes between 1.0.0-alpha5 and 1.0.0-beta1

`beta1` has **breaking public API changes**.

### Emitter Creation API Change

`clojurewerkz.eep.emitter/create` no longer uses pseudo-kwargs. So, instead of

``` clojure
(require '[clojurewerkz.eep.emitter :as eem])

(let [me (eem/create :dispatcher-type rtype :env env)]
  )
```

use the function like so

``` clojure
(require '[clojurewerkz.eep.emitter :as eem])

(let [me (eem/create {:dispatcher-type rtype :env env})]
  )
```


### Clojure 1.6

EEP now depends on `org.clojure/clojure` version `1.6.0`. It is
still compatible with Clojure 1.4 and if your `project.clj` depends on
a different version, it will be used, but 1.6 is the default now.



## Change log

[EEP change log](https://github.com/clojurewerkz/eep/blob/master/ChangeLog.md) is available on GitHub.


## EEP is a ClojureWerkz Project

EEP is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a small feature complete Clojure client for ElasticSearch
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Titanium](http://titanium.clojurewerkz.org), a Clojure graph library
 * [Meltdown](http://github.com/clojurewerkz/meltdown), a fast message passing library built on top of [Reactor](https://github.com/reactor/reactor)
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Elastisch, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
