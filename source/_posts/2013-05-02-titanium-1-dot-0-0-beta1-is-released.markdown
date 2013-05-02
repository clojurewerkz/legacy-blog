---
layout: post
title: "Titanium 1.0.0-beta1 is released"
date: 2013-05-02 22:00
comments: false
categories:
  - titanium
  - releases
---

## TL;DR

[Titanium](http://titanium.clojurewerkz.org) is a powerful Clojure graph library that is built on top of [Aurelius Titan](http://thinkaurelius.github.com/titan/).
It combines a Clojure-friendly API and graph processing DSL with the power of Titan.

`beta1` is a major development milestone that has **major public API changes**,
upgrades Titanium to Titan `0.3`, provides a separate Clojure library for
working with any Blueprints-compatible graph database and introduces
a new powerful way of querying graphs: [Ogre, a dialect of Gremlin](http://ogre.clojurewerkz.org).


## Towards Making Clojure A Great Ecosystem For Graph Analysis

When we first introduced Titanium a few months ago, the response was very positive. People
liked Titan features, swappable storage and straightforward transaction support.

Back then, Titanium wasn't the only Titan-related Clojure project on
the block. [Zack Maril](http://twitter.com/zackmaril) has been working
on another project called Hermes for a while. Then Zack [released
Ogre](https://groups.google.com/forum/?fromgroups#!searchin/gremlin-users/Ogre/gremlin-users/Del9DasqBcE/5uQEYXdLPc0J),
a Clojure library for querying [Blueprints
graphs](http://tinkerpop.com).

Titanium and Hermes were largely solving the same problem and after
discussing it for some time, we decided to join forces with Zack and
continue working together on
Titanium. [Ogre](http://ogre.clojurewerkz.org) and
[Archimedes](https://github.com/clojurewerkz/archimedes) are now
ClojureWerkz projects and Titanium `1.0.0-beta1` is based on them.

We would like to thank Zack for considering joining the team and all
the work he has been doing on Titanium and related Clojure graph libraries.

You should follow him [on Twitter](http://twitter.com/zackmaril) and
[GitHub](http://github.com/zmaril).


## Moving to Titan 0.3

Titan is still a young project and is actively being worked on. In [version 0.3](https://groups.google.com/forum/#!topic/aureliusgraphs/vlRg0ey735g),
Titan introduces several breaking API changes and new features such as

 * Full text search (indexing)
 * Better caching layer
 * Lots of optimizations
 * Properties on vertices can have properties on them which is very useful for version, timestamping, etc

Titanium closely follows these developments and `1.0.0-beta1` is based on Titan `0.3`. Not all
new Titan features are available in Titanium `1.0.0-beta1` but it won't take long.


## Improved Documentation

Titanium `1.0.0-beta1` includes a major [documentation](http://titanium.clojurewerkz.org) overhaul
to adapt to the Titan 0.3 changes and separation into multiple libraries.
In addition, [Ogre documentation site](http://ogre.clojurewerkz.org) is now also live
and uses our [standard documentation toolchain](https://github.com/clojurewerkz/docslate).

It's not a ClojureWerkz project if it is not documented well!



## Changes between Titanium 1.0.0-alpha2 and 1.0.0-beta1

### Archimedes For Working With Blueprints Graphs

Titanium now relies a separate library called [Archimedes](https://github.com/clojurewerkz/archimedes)
for graph operations on any Blueprints-compatible graph database.

### Ogre For Graph Querying

Titanium depends on [Ogre](http://ogre.clojurewerkz.org), a powerful Clojure library for querying
Blueprints-compatible graphs (a dialect of the Gremlin query language).

Ogre supercedes `clojurewerkz.titanium.gpipe` query DSL.

### Titan Types Support

In Titan, edge and vertex properties can have custom types. Titanium now
[supports said custom types](http://titanium.clojurewerkz.org/articles/types.html).

The documentation guide above provides more information.


## Change Log

[Titanium change
log](https://github.com/clojurewerkz/titanium/blob/master/ChangeLog.md)
is available on GitHub.


## News and Updates

New releases and updates are announced [on
Twitter](http://twitter.com/clojurewerkz). Titanium also has [a
mailing list](https://groups.google.com/group/clojure-titanium), feel
free to ask questions and report issues there.


## How To Follow The Development

[Titanium](https://github.com/clojurewerkz/titanium), [Ogre](https://github.com/clojurewerkz/ogre) and [Archimedes](https://github.com/clojurewerkz/archimedes) are all available on GitHub.

If you have questions about these libraries, feel free to ask on the [Titan mailing list](https://groups.google.com/group/aureliusgraphs) or [Titanium's own mailing list](https://groups.google.com/group/clojure-titanium).


## Titanium is a ClojureWerkz Project

Titanium is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Neocons](http://clojureneo4j.info), a Clojure client for the Neo4J REST API
 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Titanium, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz Team](http://twitter.com/clojurewerkz).
