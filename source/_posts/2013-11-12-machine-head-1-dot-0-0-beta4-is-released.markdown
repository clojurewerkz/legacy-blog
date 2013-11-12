---
layout: post
title: "Machine Head 1.0.0-beta4 is released"
date: 2013-11-12 04:29
comments: false
categories:
  - machine_head
  - mqtt
  - releases
---

## TL;DR

Machine Head is a small [Clojure MQTT client](http://clojuremqtt.info).

`1.0.0-beta4` is a development milestone that works around a bug in Eclipse
Paho Java.



## Changes Between 1.0.0-beta3 and 1.0.0-beta4

### Client ID Limit

MQTT spec dictates that client [ID's should be limited to
23 bytes](http://publib.boulder.ibm.com/infocenter/wmqv7/v7r0/index.jsp?topic=%2Fcom.ibm.mq.amqtat.doc%2Ftt60310_.htm). Eclipse Paho client generator [can produce ID's
longer than that](https://bugs.eclipse.org/bugs/show_bug.cgi?id=404378).

Machine Head now will limit ID length to the last 23 bytes.

Contributed by Yodit Stanton.



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
