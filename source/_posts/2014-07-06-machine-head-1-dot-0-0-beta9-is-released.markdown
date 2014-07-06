---
layout: post
title: "Machine Head 1.0.0-beta9 is released"
date: 2014-07-06 21:17:38 +0400
comments: false
categories:
  - machine_head
  - mqtt
  - rabbitmq
  - releases
---

## TL;DR

Machine Head is a small [Clojure MQTT client](http://clojuremqtt.info).

`1.0.0-beta9` is a development milestone that introduces one breaking API change.


## Changes Between 1.0.0-beta8 and 1.0.0-beta9

### Subscription API Change

Previously `clojurewerkz.machine-head.client/subscribe` accepted
a list of topics and optionally a list of QoS levels:

``` clojure
(mh/subscribe c ["mh/topics/#" "mh/alt.topics/+"]
                  (fn [^String topic meta ^bytes payload])
                  {:qos [0 1]})
```

This turns out to be a fairly confusing API.

We've changed it to accept a map of topics to QoS levels. While
a bit more verbose, this API make it very clear what topic will use
what QoS:

``` clojure
(mh/subscribe c {"mh/topics/#" 0 "mh/alt.topics/+" 1}
                  (fn [^String topic meta ^bytes payload] ))
```


## Changes Between 1.0.0-beta7 and 1.0.0-beta8

### Clojure 1.6 By Default

The project now depends on `org.clojure/clojure` version `1.6.0`. It is
still compatible with Clojure 1.4 and if your `project.clj` depends on
a different version, it will be used, but 1.6 is the default now.

We encourage all users to upgrade to 1.6, it is a drop-in replacement
for the majority of projects out there.


## Changes Between 1.0.0-beta6 and 1.0.0-beta7

### Retain Default Change

When publishing, `retain` now defaults to `false`,
which is a much more sensible default.

Contributed by Martin Trojer.


## Change Log

[Machine Head change log](https://github.com/clojurewerkz/machine_head/blob/master/ChangeLog.md)
is available on GitHub.




## Machine Head is a ClojureWerkz Project

[Machine Head](http://clojuremqtt.info) is part of the group of [Clojure libraries
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


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the
[ClojureWerkz](http://clojurewerkz.org) Team
