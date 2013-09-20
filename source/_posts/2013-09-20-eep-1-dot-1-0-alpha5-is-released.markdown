---
layout: post
title: "EEP 1.1.0-alpha5 is released"
date: 2013-09-20 21:54
comments: false
categories:
  - eep
  - releases
---

[EEP](http://blog.clojurewerkz.org/blog/2013/08/29/stream-processing-with-eep/) (Embeded Event Processing) is a Clojure stream processing library.

`1.0.0-alpha5` is a development milestone that introduces
several minor API improvements and bug fixes.


## Changes between 1.0.0-alpha4 and 1.0.0-alpha5

### Fixed a problem with repeated emitter evaluation

`build-topology` had a bug that caused emitter given in the form of `(create)` to be
re-evaluated each time the topology was updated. The bug does not affect codebases
that use a single emitter instance bound to an existing var.

### Fixed a problem with `add-handler` not returining an instance of emitter

Usually an emitter is stored in a var, but if you use a threading
macro such as `->` to build topologies, `add-handler` failed because
it returned a caching registry. Thew new version returns the emitter,
allowing for threading macros to work.

### Optional `downstreams` argument for properly visualising splitters.

Because splitters only receives a function that's responsible for the
routing, it's impossible for EEP to know where the events are routed
after split. You can define a splitter with an array of all possible
splits to make data flow visualisation possible.

For exmaple, following splitter will split events to even and odd ones. Along with
splitter function, pass an vector of `[:even :odd]` so that visualiser would catch it.

```clj
(defsplitter *emitter* :entrypoint (fn [i] (if (even? i) :even :odd)) [:even :odd])
```

## Changes between 1.0.0-alpha3 and 1.0.0-alpha4

### Meltdown is updated to 1.0.0-aplha3

Meltown alpha3 is a release with minor API additions.

### Fixed problem with RingBuffer dispatcher overflow

RingBuffer operates in it's own pool, adding notifications blocks RingBuffer's yielding,
therefore `notify` function block forever.

EEP now has realistic throughput tests that verify that the issue is gone.

### Added more options to emitter constructor

It is now possible to pass backing Dispatcher for reactor that's handling routing for the
Emitter and an environment.


## Change log

[EEP change log](https://github.com/clojurewerkz/eep/blob/master/ChangeLog.md) is available on GitHub.


## EEP is a ClojureWerkz Project

EEP is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a small feature complete Clojure client for ElasticSearch
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Titanium](http://titanium.clojurewerkz.org), a Clojure graph library
 * [Meltdown](http://github.com/clojurewerkz/meltdown), a fast message passing library built on top of [Reactor](https://github.com/reactor/reactor)
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Elastisch, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
