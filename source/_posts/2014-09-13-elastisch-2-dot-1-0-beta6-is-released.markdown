---
layout: post
title: "Elastisch 2.1.0-beta6 is released"
date: 2014-09-13 23:15:19 +0400
comments: false
categories:
  - elastisch
  - releases
---

## TL;DR

Elastisch is a battle tested, small but feature rich and well
documented [Clojure client for ElasticSearch](http://clojureelasticsearch.info). It supports
virtually every Elastic Search feature and has [solid documentation](http://clojureelasticsearch.info).

[2.1.0-beta6](https://clojars.org/clojurewerkz/elastisch/versions/2.1.0-beta6) is a preview
release of Elastisch 2.1.


## Changes between Elastisch 2.1.0-beta5 and 2.1.0-beta6

### New Line in Multi-Search REST API

ElasticSearch Multi Search REST API endpoint is sensitive to the trailing new line.
When it is missing, the response contains one result too few.

Elastisch now makes sure to append a new line to Multi Search request
bodies.

### Correct async-put in Native Client

Native client's `document/async-put` no longer fails with an exception.

Contributed by Nikita Burtsev.

### clj-time 0.8.0

[clj-time](https://github.com/clj-time/clj-time) dependency has been upgraded to version 0.8.0.


## Full Change Log

[Elastisch change log](https://github.com/clojurewerkz/elastisch/blob/master/ChangeLog.md) is available on GitHub.


## Elastisch is a ClojureWerkz Project

[Elastisch](http://clojureelasticsearch.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client
 * [Titanium](http://titanium.clojurewerkz.org), a Clojure graph library
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Elastisch, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
