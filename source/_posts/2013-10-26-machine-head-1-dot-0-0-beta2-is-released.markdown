---
layout: post
title: "Machine Head 1.0.0-beta2 is released"
date: 2013-10-26 14:12
comments: false
categories: 
 - machine_head
 - mqtt
 - releases
---

## TL;DR

Machine Head is a small [Clojure MQTT client](http://clojuremqtt.info).

`1.0.0-beta2` is a development milestone which refines the API and has breaking
changes.



## Changes between Machine Head 1.0.0-beta1 and 1.0.0-beta2

### `client/subscribe-with-qos` is Removed

`clojurewerkz.machine-head.client/subscribe-with-qos` is removed. Instead,
`clojurewerkz.machine-head.client/subscribe` now takes a new option, `:qos`.

Contributed by Martin Trojer.


## Change Log

[Machine Head change
log](https://github.com/clojurewerkz/machine_head/blob/master/ChangeLog.md)
is available on GitHub.




## Machine Head is a ClojureWerkz Project

[Machine Head](http://clojuremqtt.info) is part of the [group of libraries
known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Cassaforte](http://clojurecassandra.info), a Cassandra client built around CQL 3
 * [Neocons](http://clojureneo4j.info), a feature rich Clojure client for Neo4J REST API

and several others. If you like Machine Head, you may also like [our other
projects](http://clojurewerkz.org).

Let us know what you think [on
Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing
list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the
[ClojureWerkz](http://clojurewerkz.org) Team
