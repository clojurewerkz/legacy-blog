---
layout: post
title: "Neocons 1.1.0-beta3 is released"
date: 2013-02-06 17:42
comments: false
categories:
  - neocons
  - releases
---
## TL;DR

Neocons is a feature rich idiomatic [Clojure client for the Neo4J REST API](http://clojureneo4j.info).

`1.1.0-beta3` is a preview `1.1.0` release that is *100% backwards-compatible* with `1.0.x`.



## Changes between Neocons 1.1.0-beta2 and 1.1.0-beta3

### Correct URI Path Encoding

Neocons now correctly encodes all parts of URIs, which means
index keys and values can contain whitespace and Unicode
characters, for example.

GH issue: [#20](https://github.com/michaelklishin/neocons/issues/20)

### clj-http upgraded to 0.6.4

Neocons now uses clj-http 0.6.4.

### Support upgraded to 0.12.0

Neocons now uses ClojureWerkz Support 0.12.0.



## Change Log

We recommend all users to give [1.1.0-beta3](https://clojars.org/clojurewerkz/neocons/versions/1.1.0-beta3) a try.

[Neocons change log](https://github.com/michaelklishin/neocons/blob/master/ChangeLog.md) is available on GitHub.



## Neocons is a ClojureWerkz Project

[Neocons](http://clojureneo4j.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](https://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](https://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Monger](https://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Welle](https://clojureriak.info), a Riak client with batteries included
 * [Quartzite](https://clojurequartz.info), a powerful scheduling library

and several others. If you like Neocons, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
