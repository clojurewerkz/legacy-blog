---
layout: post
title: "Introducing Titanium"
date: 2013-02-11 17:00
comments: false
categories:
  - titanium
  - releases
---

## TL;DR

[Titanium](http://titanium.clojurewerkz.org) is a powerful Clojure graph library that is built on top of [Aurelius Titan](http://thinkaurelius.github.com/titan/).
It combines a Clojure-friendly API and graph processing DSL with the power of Titan.


## The Quest To Improve

[ClojureWerkz projects](http://clojurewerkz.org) are mostly known for our data store clients. Data processing is a
sweet spot for Clojure and that's what we primarily use it for.

Over time we've developed and released a number of data store clients:

 * [Monger](http://clojuremongodb.info)
 * [Neocons](http://clojureneo4j.info)
 * [Welle](http://clojureriak.info)
 * [Elastisch](http://clojureelasticsearch.info)

and a few others.

Some of them work very well and we will likely be happy with them for years
to come. However, with some projects we keep thinking there is a limit to their
usefullness or application. Sometimes the limitations are completely outside
of our control, for example, licensing or implementation details of dependencies.


## Standing On The Shoulders of Giants

Fortunately, the open source community is moving fast and new data stores are
being released every year. Last year folks from [Aurelius](thinkaurelius.com) released
[Titan](http://thinkaurelius.github.com/titan/), a new powerful graph library that
has pluggable storage backends and nails a few problems we've been having with
other graph data stores.

Titan is primarily used as a JVM library which is significantly more
efficient than issuing HTTP requests all the time when you are busy
populating or updating the graph from an ongoing flow of events in the
same JVM (e.g. a Web crawler activity). In addition, it can use
[Cassandra](http://cassandra.apache.org) or
[HBase](http://hbase.apache.org) for durable storage, largely
eliminating operations-related limitations (backup tools, HA) in some
other popular open source graph data stores.

As Titan was getting more and more mature, we kept evaluating it and
discussing what a good Clojure library on top of it would look like.

Today we are happy to release some results of that thinking.


## Introducing Titanium

[Titanium](http://titanium.clojurewerkz.org) is a powerful Clojure graph library that is built on top of [Aurelius Titan](http://thinkaurelius.github.com/titan/).
It combines a Clojure-friendly API and graph processing DSL with the power of Titan:

 * [BerkeleyDB](https://github.com/thinkaurelius/titan/wiki/Using-BerkeleyDB), [Cassandra](https://github.com/thinkaurelius/titan/wiki/Using-Cassandra) or [HBase](https://github.com/thinkaurelius/titan/wiki/Using-HBase) for storage
 * Powerful features of the [Tinkerpop graph technologies stack](http://tinkerpop.com)
 * Linear scalability, large number of concurrent users
 * Good performance (throughput, latency) baseline
 * Transaction support
 * Apache Public License 2.0

Today we release a very early version, [1.0.0-alpha1](https://clojars.org/clojurewerkz/titanium/versions/1.0.0-alpha1).


## What's In The Box

In `1.0.0-alpha1`, with Titanium you can 

 * Populate the graph (add vertices, edges)
 * Manipulate properties of vertices and edges
 * Define indexes for graph elements
 * Query the graph using key/value lookups
 * Query and traverse the graph via a (semi-complete) DSL powered by [Gremlin and Pipes](https://github.com/tinkerpop/gremlin/wiki/Using-Gremlin-through-Java)
 * Configure Titan graphs

all via easy to use, Clojuric API.



## Documentation & Examples

Because this is a ClojureWerkz project, we could not make this release
public without at least one complete [documentation
guide](http://titanium.clojurewerkz.org).

[Titanium's test
suite](https://github.com/clojurewerkz/titanium/tree/master/test/clojurewerkz/titanium)
can be used to get more code examples.



## Development, Issue Tracking, Supported Clojure Versions

Titanium targets Clojure 1.3+ and tested against 3 Clojure versions (`1.4`, `1.3`, `1.5-master-SNAPSHOT`) x 3 JDKs (OpenJDK 7, Oracle JDK 7, OpenJDK 6).

The source is available [on
GitHub](http://github.com/clojurewerkz/titanium). We also use GitHub
to track issues. If you want to contribute, there is a section on our
workflow [in the
README](https://github.com/clojurewerkz/titanium/blob/master/README.md#development).


## License

Titanium is double-licesned under the [Eclipse Public
License](http://www.eclipse.org/legal/epl-v10.html) (the same as
Clojure) and the [Apache Public License
2.0](http://www.apache.org/licenses/LICENSE-2.0.html) (the same as
Titan).



## What's Ahead

We definitely want Titanium to be feature complete and get more powerful as Titan
itself gets more powerful and mature. [The Tinkerpop stack](http://tinkerpop.com) has a lot
to offer and a lot of potential to grow into the industry standard graph technologies stack
(at least on the JVM). Titanium will take full advantage of that.

We also think Titanium can grow to offer useful features of its
own. There is a lot of work ahead even to catch up with Titan, but we
already have a few ideas.  Our short term goal is to make Titanium
reach rough feature parity with [Neocons](http://clojureneo4j.info)
and expose all the good parts of Titan.

Needless to say, documentation guides will only get better.



## News and Updates

New releases and updates are announced [on
Twitter](http://twitter.com/clojurewerkz). Titanium also has [a
mailing list](https://groups.google.com/group/clojure-titanium), feel
free to ask questions and report issues there.


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
