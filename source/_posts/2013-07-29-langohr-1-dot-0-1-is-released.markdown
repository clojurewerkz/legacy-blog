---
layout: post
title: "Langohr 1.0.1 is released"
date: 2013-07-29 09:41
comments: false
categories:
  - langohr
  - releases
---

## TL;DR

Langohr is a [Clojure RabbitMQ client](http://clojurerabbitmq.info) that embraces [AMQP 0.9.1 Model](http://www.rabbitmq.com/tutorials/amqp-concepts.html).

With `1.0.1`, Langohr is finally a `1.0` library, after 2 years in the making.


## Time for 1.0

Langohr is the original ClojureWerkz library, started in late July 2011. It had quickly reached a point when it was
useful enough. With the help of our users, there were 3-4 releases with breaking changes and major usability
improvements.

Since 2013, Langohr has not changed much. It has [decent documentation](http://clojurerabbitmq.info), has been in
use by many people we know and supports every feature RabbitMQ 3.1 provides.

So while it is still missing a couple of hard to get right features, the `1.0` release has been long overdue.
After all, some of much younger libraries are at 1.6 or 1.5 already.

`1.0.1` is basically `1.0.0-beta14` with a different version and one typo fix.


## Changes between Langohr 1.0.0-beta14 and 1.0.1

### langohr.shutdown/sort-error? => langohr.shutdown/soft-error?

`langohr.shutdown/soft-error?` is now correctly named.

Contributed by Ralf Schmitt.


## Getting Help

If you have any questions about Langohr, feel free to [join our mailing list](https://groups.google.com/forum/#!forum/clojure-rabbitmq) and [rabbitmq-discuss](https://lists.rabbitmq.com/cgi-bin/mailman/listinfo/rabbitmq-discuss)
or stop by `#rabbitmq` channel on irc.freenode.net.



## Plans for the Future

We are already working on a major feature for Langohr 1.1: automatic connection recovery, similar to what
a couple of Ruby clients support. Features like this take a while to develop but the progress so far
is promising.

We'll keep you posted!



## Change Log

[Langohr change log](https://github.com/michaelklishin/langohr/blob/master/ChangeLog.md) is available on GitHub.


## Langohr is a ClojureWerkz Project

[Langohr](http://clojurerabbitmq.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Elastisch](http://clojureelasticsearch.info), a minimalistic well documented Clojure client for ElasticSearch
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Langohr, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
