---
layout: post
title: "Introducing Meltdown"
date: 2013-09-04 00:21
comments: false
categories:
  - meltdown
  - releases
---

## Can You Please Pass Me a Message?

Last week we introduced a new project we've been working on for
a few months, [EEP](/blog/2013/08/29/stream-processing-with-eep/).

To make event processing concurrent and parallel, there needs
to be a way to transfer events (messages) from threads that
produce them to threads that consume them. In addition,
it is desirable to also be able to filter events
consumers are interested in.

There are multiple message passing libraries available on the JVM.
Some of them are stable and very mature but have very small
contributor base, others are extremely actively used but less
convenient to consume from Clojure, some do not offer some of
the features we wanted. So we decided to wait and see, and
not make the choice yet.

## Enter Reactor

This move turned out to be the right one: a couple of months after
the first EEP prototype was put up on GitHub to ask for some feedback
from our friends (hi, Darach!), folks at [Pivotal](http://gopivotal.com)
[introduced Reactor](http://blog.springsource.org/2013/05/13/reactor-a-foundation-for-asynchronous-applications-on-the-jvm/), a "foundational framework for asynchronous programming
on the JVM".

Reactor core is an event (message) passing library that has several
features that we found very handy for stream processing:

 * Consumer may consume events selectively (events have routing keys)
 * Message passing implementation is pluggable
 * It's very easy to run multiple reactors in the same JVM
 * It can be backed by [LMAX Disruptor](http://lmax-exchange.github.io/disruptor/),
   which offers very high throughput *and* really low stable latency
   thanks to smart false sharing elimination techniques

After seeing that it only took 2 hours to write a first Meltdown version
with some tests, we were convinced Reactor is a great choice for our
needs.

## Meltdown Goes to School

Since Reactor was a really young project by the time we started
using it (we may have been the first people outside of Pivotal
who have built something on top of Reactor at that point),
it took a few iterations and serious breaking API changes
in both libraries until we've been confident enough to port
EEP to it.

In the end it took Alex a few hours to make the switch,
which again demonstrates how well Reactor and Meltdown
fit EEP.

## The Future of Meltdown

Meltdown still does not cover all of Reactor's functionality and
Reactor is under active development, so Meltdown will stay
alpha for some time. Since we've announced it here, we will do
our best with writing some initial documentation guides
for it.

In the meantime, feel free to give Meltdown a try. Check it out
in the REPL, try modeling a problem that needs message passing
with it. It likely will already take you a long way (except
for the really poor documentation).

You can watch our progress [on
GitHub](http://github.com/clojurewerkz/meltdown) and follow the news
[on Twitter @clojurewerkz](http://twitter.com/clojurewerkz).


## Meltdown is a ClojureWerkz Project

[Meltdown](http://github.com/clojurewerkz/meltdown) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client built around CQL
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [EEP](http://github.com/clojurewerkz/eep), a Clojure event processing library
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like EEP, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[@michaelklishin](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
