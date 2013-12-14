---
layout: post
title: "Machine Head 1.0.0-beta5 is released"
date: 2013-12-12 22:11
comments: false
categories:
  - machine_head
  - mqtt
  - releases
---

## TL;DR

Machine Head is a small [Clojure MQTT client](http://clojuremqtt.info).

`1.0.0-beta5` is a development milestone that support for MQTT Last Will and Testament.



## Changes Between 1.0.0-beta4 and 1.0.0-beta5

### Last Will and Testament

Machine Head now supports providing client last will and testament:

``` clojure
(require '[clojurewerkz.machine-head.client :as mh])

(let [will {:topic "lw-topic" :payload (.getBytes "last will") :qos 0 :retain false}]
  (mh/connect "" (mh/generate-id) {:will will}))
```

Contributed by Paul Bellamy.


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
