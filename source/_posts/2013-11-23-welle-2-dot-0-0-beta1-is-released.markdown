---
layout: post
title: "Welle 2.0.0-beta1 is released"
date: 2013-11-23 13:00
comments: false
categories:
  - welle
  - riak
  - releases
---

## TL;DR

Welle is an expressive [Clojure client for Riak](http://clojureriak.info) with batteries included.

[2.0.0-beta1](https://clojars.org/com.novemberain/welle/versions/2.0.0-beta1) is a development release
of 2.0 that *has breaking API changes* and introduces an important bug fix, dependency updates
and support for Riak 1.4 counters.


## Changes between Welle 1.5.0 and 2.0

Welle 2.0 has **breaking API changes** in `clojurewerkz.welle.kv` functions.

### Changes in K/V Function Return Values

This is a **breaking API change**.

Welle 2.0 changes how Riak responses are represented as Clojure maps.
Welle now will correctly preserve all vector clocks associated with multiple
siblings in the response and the response itself.

This means that `welle.kv/modify` will work correctly and won't make sibling
explosions worse.

The most important part of the change is how responses are represented:
every response is an immutable map that has `:result` key as well as other
metadata keys (`:has-value?`, `:has-siblings?`, `:modified?`, `:content-type` and so on).

This contrasts with earlier versions, where results were returned directly by functions
such as `welle.kv/fetch`, it is now possible to destructure the response in order to
obtain the returned value:

``` clojure
(require '[clojurewerkz.welle.kv :as kv])

(let [{:keys [result] :as m} (kv/fetch bucket-name k :r 1)]
  (comment "Do something with the result"))
```

Here are the keys that `clojurewerkz.welle.kv/fetch` returns now for every response:

 * `:result`: one or more objects returned by Riak
 * `:vclock`: vector clock of the response
 * `:has-siblings?`: true if response has siblings
 * `:has-value?`: true if response is non-empty
 * `:modified?`: false when conditional GET returned a non-modified response
 * `:deleted?`: true if this object has been deleted but there is a vclock for it

### Clojure 1.3 Support Dropped

Welle no longer supports Clojure 1.3.

### Counters Support (Riak 1.4+)

`clojurewerkz.welle.counters` is a new namespace that provides operations on [Riak counters](http://basho.com/counters-in-riak-1-4/):

``` clojure
(require '[clojurewerkz.welle.counters :as wcnt])

(let [bucket-name "counters"
      counter     "hit-points"]
  (wcnt/increment-counter bucket-name counter)
  ;= 1
  (wcnt/fetch-counter bucket-name counter)
  ;= 1
  (wcnt/increment-counter bucket-name counter :value 2))
  ;= 3
  (wcnt/increment-counter bucket-name counter :value -3))
  ;= 0
```

### Riak Java Client Update

Welle now uses Riak Java client [1.4.2](https://github.com/basho/riak-java-client/blob/1.4.2/CHANGELOG).

### Cheshire Update

Cheshire has been updated to `5.2.0`.

### clj-http Update

clj-http has been updated to `0.7.7`.

### Support Update

ClojureWerkz Support has been updated to `0.20.0`.

### Ports Support in PB Cluster Client

While creating a protocol buffer cluster client you can now provide
hosts and ports separated by a colon, e.g. "127.0.0.1:10017". If a port is not
provided, the default port will be used.

So now you can use following format:

``` clojure
(wc/connect-to-cluster-via-pb! ["10.0.1.2",
			        "10.0.1.3",
				"10.0.1.4",
				"10.0.1.5",
				"10.0.1.6"])

as well as following format:

``` clojure
(wc/connect-to-cluster-via-pb! ["127.0.0.1:10017",
			        "127.0.0.1:10027",
				"127.0.0.1:10037",
				"127.0.0.1:10047"])
```


### Validateur Dependency Dropped

[Validateur](http://clojurevalidations.info) is no longer a dependency of Welle.

Don't worry, they still work well together.

### Optional Keywordization of Keys With JSON Serialization

Automatic JSON serialization previously unconditionally converted keys to keywords.
This may be a problem for some projects, because keywords are not garbage collected.

`clojurewerkz.welle.conversion/*convert-json-keys-to-keywords*` is a new dynamic var that
controls this behavior. When bound to false, automatic JSON serialization won't convert
keys to keywords.




## Change Log

We recommend all users to give [2.0.0-beta1](https://clojars.org/com.novemberain/welle/versions/1.5.0) a try.

[Welle change log](https://github.com/michaelklishin/welle/blob/master/ChangeLog.md) is available on GitHub.



## Welle is a ClojureWerkz Project

[Welle](http://clojureriak.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](http://clojureneo4j.info), a feature rich idiomatic Clojure client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Welle, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


## Donations

ClojureWerkz [accepts donations](http://clojurewerkz.org/articles/donate.html). If you feel like our projects save you time, consider donating. Thanks.


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
