---
layout: post
title: "What's Going on With Titanium"
date: 2013-04-17 21:17
comments: false
categories: 
  - titanium
---

After we [announced Titanium](http://blog.clojurewerkz.org/blog/2013/02/11/introducing-titanium/), our Clojure library on top of [Titan](http://titan.thinkaurelius.com), back in mid-February, there hasn't been
much activity related to it. Let us explain what's going on with it and where the project is headed.


## Joining Forces With Zack Maril

Titanium wasn't the only Titan-related Clojure project on the block. [Zack Maril](http://twitter.com/zackmaril) has been working on another project called
Hermes for a while. Then Zack [released Ogre](https://groups.google.com/forum/?fromgroups#!searchin/gremlin-users/Ogre/gremlin-users/Del9DasqBcE/5uQEYXdLPc0J), a Clojure library for querying [Blueprints graphs](http://tinkerpop.com).

Titanium and Hermes were largely solving the same problem and after
discussing it for some time, we decided to join forces with Zack and
continue working together on
Titanium. [Ogre](http://ogre.clojurewerkz.org) and
[Archimedes](https://github.com/clojurewerkz/archimedes) are now
ClojureWerkz projects and Titanium `1.0.0-beta1`, which will be
shipped after the docs are finalized, will be based on them.

We would like to thank Zack for considering joining the team and all the work he has been doing on Titanium, Ogre and
Archimedes in the last few weeks. You should follow him [on Twitter](http://twitter.com/zackmaril) and [GitHub](http://github.com/zmaril).


## Upgrading to Titan 0.3

Titan is actively being worked on. In [version 0.3](https://groups.google.com/forum/#!topic/aureliusgraphs/vlRg0ey735g), Titan introduces several breaking API changes and new features
such as

 * Full text search (indexing)
 * Better caching layer
 * Lots of optimizations
 * Properties on vertices can have properties on them which is very useful for version, timestamping, etc

Titanium closely follows these developments. This also means that
`beta1` will introduce quite a few breaking API changes over `alpha2`. Fortunately, the earlier in project
history we do these changes, the easier it will be for Titanium users.


## Improving Documentation

Taking Titanium `1.0.0-beta1` included a major documentation overhaul to adapt to the Titan 0.3 changes. In addition,
we are porting Ogre documentation to our [standard documentation site template](https://github.com/clojurewerkz/docslate) and keep expanding the docs.

It's not a ClojureWerkz project if it is not documented well!



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

and several others. If you like Titanium, you may also like [our other projects](http://clojurewerkz.org). We also [accept donations](http://clojurewerkz.org/articles/donate.html).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).



[@michaelklishin](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
