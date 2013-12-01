---
layout: post
title: "Introducing Buffy"
date: 2013-11-29 23:18
comments: true
categories:
  - buffy
  - releases
---

## Buffy The Byte Buffer Slayer

[Buffy](https://github.com/clojurewerkz/buffy) is a Clojure library to working with binary data, writing complete
binary protocol implementations in Clojure, storing complex data
structures in an off-heap cache, reading binary files and doing everything
you would usually do with byte buffers.

Buffy is built on top of Netty byte buffers, which addresses many of the issues
with `java.util.ByteBuffer`.

## Main features

Buffy enables you to access buffers in the similar way you work with
the regular Clojure data structures. You can get and set fields separately from one
another, give names to different parts of binary representation and so on:

  * partial deserialization (read and deserialise parts of a byte buffer)
  * named access (access parts of your buffer by names)
  * composing/decomposing from key/value pairs
  * pretty hexdump
  * many useful default types that you can combine and extend easily

## Data Types

Data types used in Buffy buffers include:

  * primitives, such as `int32`, `boolean`, `byte`, `short`, `medium`, `float`, and `long`
  * arbitrary-length `string`
  * byte arrays
  * composite types (combine multiple primitive values together)
  * repeated type (repeat any primitive arbitrary amount of times in payload)
  * enum type (for mapping between human-readable and binary representation of constants)

## The Future of Buffy

Buffy has been serving us well for some time, and no major issues were
revealed. However, until it reaches GA, we can't rule breaking API changes out.

We are also very much behind on documentation.


## Buffy is a ClojureWerkz Project

[Buffy](http://github.com/clojurewerkz/buffy) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client built around CQL
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [EEP](http://github.com/clojurewerkz/eep), a Clojure event processing library
 * [Meltdown](http://github.com/clojurewerkz/meltdown), Clojure interface to Reactor
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Buffy, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[@ifesdjeen](http://twitter.com/ifesdjeen) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
