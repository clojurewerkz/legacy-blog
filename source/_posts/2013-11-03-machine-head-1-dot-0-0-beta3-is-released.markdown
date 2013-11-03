---
layout: post
title: "Machine Head 1.0.0-beta3 is released"
date: 2013-11-03 23:13
comments: false
categories:
  - machine_head
  - mqtt
  - releases
---

## TL;DR

Machine Head is a small [Clojure MQTT client](http://clojuremqtt.info).

`1.0.0-beta3` is a development milestone which exposes a minor feature
in the Paho Java client.



## Changes between Neocons 1.0.0-beta2 and 1.0.0-beta3

### Clean Session Support

`clojurewerkz.machine-head.client/connect` now supports one more
option: `:clean-session`. When set to true, the option means that
the client and MQTT broker should discard state that might have
been kept from earlier connections.


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
