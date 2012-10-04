---
layout: post
title: "Announcing Langohr documentation guides"
date: 2012-10-04 17:32
comments: true
categories: langohr, documentation
---

## TL;DR

Langohr is a [RabbitMQ Clojure client](http://clojurerabbitmq.info) that embraces [AMQP 0.9.1 model](http://bit.ly/amqp-model-explained). 

While Langohr is not yet quite ready for 1.0, it is past all major breaking changes and [the doc site](http://clojurerabbitmq.info) are in good enough shape to
announce them.


## A Brief History Lesson

Langohr is a [RabbitMQ Clojure client](http://clojurerabbitmq.info) that embraces [AMQP 0.9.1 model](http://bit.ly/amqp-model-explained).
ClojureWerkz started with Langohr and it has served us well over the last 16 months or so. Before starting Langohr, ClojureWerkz core team members already had
years of experience working with (and on) 3 other RabbitMQ clients:

 * [amqp gem](http://github.com/ruby-amqp/amqp)
 * the official Java client
 * [Hot Bunnies](http://github.com/ruby-amqp/hot_bunnies)

However, up until now it's lacked the key feature ClojureWerkz projects share: documentation guides. Fortunately, not any more.



## Langohr Documentation Guides Are Here!

There is a good thing about starting Langohr documentation work later: Langohr benefits from [amqp gem documentation guides](http://rubyamqp.info)
that we've gotten good feedback on. In the end we decided to adapt amqp gem guides for Langohr, revisit and edit them and contribute any
improvement that come to mind back to the Ruby client documentation.

Today we are happy to report that most of the work is already done and [available at clojurerabbitmq.info](http://clojurerabbitmq.info):

### [Getting started](http://clojurerabbitmq.info/articles/getting_started.html)

This is your typical Getting Started guide, covering things like RabbitMQ installation, adding Langohr as a dependency to your project,
basic concepts and a few examples to demonstrate key features:

 * The "Hello, world" of messaging
 * Blabbr, a Twitter-like one-to-many topology example
 * Weathr, an n-to-m topology example


### [AMQP Concepts](http://www.rabbitmq.com/tutorials/amqp-concepts.html)

This article covers AMQP 0.9.1 model, concepts and protocol structure. It is not client-specific and now lives on rabbitmq.com so we simply link to it.


### [Conneciting To The Broker](/articles/connecting.html)

This guide covers:

 * How to connect to RabbitMQ with Langohr
 * How to use connection URI to connect to RabbitMQ (also: on Heroku)
 * How to open a channel
 * How to close a channel
 * How to disconnect


### [Queues and Consumers](http://clojurerabbitmq.info/articles/queues.html)

This is the key article for applications that primarily consume messages.

For example:

 * How to declare AMQP queues with Langohr
 * Queue properties
 * How to declare server-named queues
 * How to declare temporary exclusive queues
 * How to consume messages ("push API")
 * How to fetch messages ("pull API")
 * Message and delivery properties
 * Message acknowledgements
 * How to purge queues
 * How to delete queues
 * Other topics related to queues


### [Exchanges and Publishing](http://clojurerabbitmq.info/articles/exchanges.html)

This is another long article that covers multiple topics relavant for apps that mostly produce messages.

It covers:

 * Exchange types
 * How to declare AMQP exchanges with Langohr
 * How to publish messages
 * Exchange propreties
 * Fanout exchanges
 * Direct exchanges
 * Topic exchanges
 * Default exchange
 * Message and delivery properties
 * Message routing
 * Bindings
 * How to delete exchanges
 * Other topics related to exchanges and publishing

Together with the Queues guide, this is the bulk of Langohr documentation.

There are also several smaller guides most of which are not yet ready. They will be added as the time permits.


## The Road To 1.0

Langohr `1.0` is still a few months away. The API is largely locked down but we take a conservative stance and try to be careful about
calling things "done". There is still a number of features we'd like to add before the big `1.0` release and a number of small documentation
guides still remain to be written.



## Thank You Contributors

We would like to thank people who have helped make Langohr documentation better by reviewing our drafts, suggesting improvements, correcting
the grammar and simply encouraging us to take this project through to completion:

 * [Theo Hultberg](https://twitter.com/iconara)
 * [Álvaro Videla](https://twitter.com/old_sound)
 * [Chris Duncan](https://twitter.com/celldee) (for editing the original amqp gem guides)

If you'd like to contribute, all the docs are [open source and available on GitHub](https://github.com/clojurewerkz/langohr.docs). Fork away and
submit us a pull request when you are done.


## News and Updates

If you'd like to follow Langohr progress, new releases and updates are announced [on Twitter](http://twitter.com/clojurewerkz).
Langohr also has [a mailing list](https://groups.google.com/group/clojure-langohr), feel free to ask questions and report issues there.



## Langohr is a ClojureWerkz Project

Langohr is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Elastisch](https://clojureelasticsearch.info), a minimalistic well documented Clojure client for ElasticSearch
 * [Welle](https://clojureriak.info), a Riak client with batteries included
 * [Monger](https://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](https://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](https://clojurequartz.info), a powerful scheduling library

and several others. If you like Langohr, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


The [ClojureWerkz](http://clojurewerkz.org) Team
