---
layout: post
title: "The Future of Neocons"
date: 2013-03-16 22:32
comments: false
categories:
  - neocons
---

## A Bit of History

[Neocons](http://clojureneo4j.info) was started in late 2011 because there was no
Clojure client for Neo4J Server that we were happy with.

Neocons reached `1.0` in July 2012. Thanks to [solid documentation](http://clojureneo4j.info),
it quickly gathered several users besides its original developers and was generally
well received.

Ever since then people contributed ideas, bug fixes and features. Neocons moved in small
steps and we tried hard to keep things backwards-compatible. `1.1` was released in March 2013
and (as far as we know) is a drop-in replacement for `1.0.x`.

This incremental releases philosophy is appreciated by the Clojure community. Clojure
itself does not try to pack features as fast as possible. Many things are introduced
into the language literally years after they were first discussed. This is a good thing
and that's why so many codebases can go from `1.3` to `1.4` and then to `1.5` without
any changes.

However, every once in a while you need to have some freedom to make sweeping changes.


## Looking To The Future

Not so long ago a little birdie told us about what's coming in Neo4J Server 2.0. We cannot
share it in this post but it is nice and may require breaking API changes in client
libraries. That's why the next non-bugfix release of Neocons will be `2.0`.

It will target Neo4J Server `2.0`. For `1.1`, we wanted to move most of the code
to use the [Cypher language](http://docs.neo4j.org/chunked/stable/cypher-query-lang.html). Unfortunately, Cypher still has several limitations
([one example](https://github.com/neo4j/neo4j/issues/340)) that do not let us do that. But it is still a good idea and we will
try to get there with `2.0`.


## What Does It Mean For You?

We will try to keep Neocons `2.0` backwards compatible if we can. ClojureWerkz
maintainers care about backwards compatibility and hate changes app code for no
good reason as much as you do.

However, there's always a possibility that the awesome Neo4J team will pack `2.0`
with features so sweet, we will have to re-focus the library around them.

Time will tell!


## Neocons is a ClojureWerkz Project

[Neocons](http://clojureneo4j.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Neocons, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
