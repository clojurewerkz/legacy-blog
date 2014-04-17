---
layout: post
title: "Meltdown 1.0.0-beta10 is released"
date: 2014-04-18 03:00:51 +0400
comments: false
categories:
  - reactor
  - releases
---

## TL;DR

Meltdown is a Clojure interface to [Reactor](https://github.com/reactor), an asynchronous
programming, event passing and stream processing [toolkit for the JVM](http://spring.io/blog/2013/11/12/it-can-t-just-be-big-data-it-has-to-be-fast-data-reactor-1-0-goes-ga).

`1.0.0-beta10` is a development milestone with minor improvements.



## Changes between 1.0.0-beta9 and 1.0.0-beta10

### Reactor Update

Reactor is updated to `1.1.0.M3`.


### 2-arity of clojurewerkz.meltdown.reactor/on is Removed

Reactor `1.1.0.M3` no longer supports default key (selector),
so 2-arity of `clojurewerkz.meltdown.reactor/on` was removed.


### Clojure 1.6

Meltdown now depends on `org.clojure/clojure` version `1.6.0`. It is
still compatible with Clojure 1.4 and if your `project.clj` depends on
a different version, it will be used, but 1.6 is the default now.


## Changes between 1.0.0-beta8 and 1.0.0-beta9

### Consumer and Selector Introspection

`clojurewerkz.meltdown.selectors/selectors-on` is a new function that
returns a list of selectors registered on a reactor:

``` clojure
(require '[clojurewerkz.meltdown.reactor   :as mr])
(require '[clojurewerkz.meltdown.selectors :as ms :refer [$])

(let [r   (mr/create)]
  (mr/on r ($ "a.key) (fn [evt]))
  (ms/selectors-on r))
```

`clojurewerkz.meltdown.consumers/consumer-count` is a new function that
returns a number of consumers registered on a reactor:

``` clojure
(require '[clojurewerkz.meltdown.reactor   :as mr])
(require '[clojurewerkz.meltdown.selectors :refer [$])
(require '[clojurewerkz.meltdown.consumers :as mc])

(let [r   (mr/create)]
  (mr/on r ($ "a.key) (fn [evt]))
  (mc/consumer-count r))
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
