---
layout: post
title: "The ClojureWerkz Project in 2012"
date: 2012-12-29 03:14
comments: true
categories:
  - retrospective
  - mission
---

## TL;DR

2012 was the year when most widely used ClojureWerkz libraries really matured and got traction.


## 2012 Retrospective

First line of code for a ClojureWerkz library was written on July 31st, 2011. Back then, we had no idea there will be
over a dozen more libraries to follow. Through 2012, a number of our projects have seen their 1.0 releases (and then some),
documentation guides for them (mostly) finished and plenty of feedback and improvements contributed by the community.

### Monger

Monger is our excellent [Clojure driver for MongoDB](http://clojuremongodb.info).

On June 26th, 2012, after 11 months in the making, Monger 1.0 was released. `1.1` followed the next month
and by late November, [Monger is at 1.4](http://blog.clojurewerkz.org/blog/2012/11/27/monger-1-dot-4-0-is-released/),
waiting for new MongoDB features to be shipped so that we can support them.

Monger has become stable, efficient, feature complete, easy to use and well documented, thanks to a lot of feedback
in 2012. Some users go as far as saying

> This is easily the best DB library I've used in any language. Thanks!

Now, this may be a *very* generous compliment but we feel that Monger is a mature library and an example to
follow for other ClojureWerkz libraries and open source projects in general.


### Neocons

Neocons is a [Clojure client for Neo4J REST API](http://clojureneo4j.info).

Neocons `1.0` was released on July 15th, 2012, after about 9 months in the works. Judging from our users'
feedback, Neocons is the library that sparkles most passionate comments. From a Neocons user:

> Your clojurewerkz stuff in general is really improving my Clojure experience, which is rapidly becoming my language of choice

Good stuff!


### Welle

Welle is an expressive [Clojure client for Riak](http://clojurewelle.info) with batteries included. Welle was first major
ClojureWerkz library to reach the `1.0` mark in May 2012. Personally, Welle is my favorite ClojureWerkz library:
there is next to nothing you can remove from it and not that can be added as well. Of course, there are new
Riak releases ahead and Welle will be sure to support them in the future!


### Elastisch

Elastisch is a minimalistic [Clojure client for ElasticSearch](http://clojureelasticsearch.info).

`1.0` since September 2012, Elastisch documentation is something we still cannot believe we could pull off. There is enough
content for a little book on ElasticSearch, and we are far from being completely happy with it!

A couple of quotes from Elastisch users:

> Elastisch is beyond awesome

> Speaking of, Elastisch (and its docs) = changed my life. Kudos.

Just another proof how much betthe user experience can be if you put aside all excuses and document your open source
project really well.


### Langohr

Langohr is a [Clojure RabbitMQ client](http://clojurerabbitmq.info) that embraces [AMQP 0.9.1 Model](http://www.rabbitmq.com/tutorials/amqp-concepts.html).

Although Langohr is the oldest ClojureWerkz project, it hasn't reached `1.0` yet. It has, however, gone through a number of breaking
changes after real world feedback and is shaping up nicely, including the docs.

We are finishing adding RabbitMQ HTTP API support to it in the near future.


## Thank You, Contributors

Nearly all of our projects have contributions from the broader Clojure community. From full-blown features to documentation improvements
to bug fixes to benchmark results to ideas that turn into improvements. Thank you very much, there is no way
[Michael](http://twitter.com/michaelklishin) and [Alex](http://twitter.com/ifesdjeen) could do all this work on their own.


## Here's To 2013

What should you expect from ClojureWerkz in 2013? More of what our values are: feature complete, well documented,
well maintained Clojure libraries compatible with multiple Clojure versions (1.3+). Clojure 1.5 compatibility is already
ready, waiting to be shipped when Clojure 1.5 final ships.

But there's more. After seeing a lot of positive feedback on the [Clojure Documentation Site](http://clojure-doc.org), in which
[Michael](http://twitter.com/michaelklishin) is actively taking part, we decided that there's a bigger fish for us to catch.
Developing libraries is important but empowering more people to develop better libraries is going to help the Clojure ecosystem
a lot more. This is why you can expect more CDS and documentation efforts from us in the future. For example, our projects
use many Clojure features that can be demonstrated better when put into a context: a series of blog posts about them
is one example of how we can help improve Clojure documentation.

Something else we have a lot to share about is library development and maintenance. With about 20 libraries, all compatible with 3
Clojure versions, under our belt, we believe we know a thing or two about how to (and how *not to*) maintain
an open source project.

If any of this sounds exciting, follow [ClojureWerkz updates](http://twitter.com/clojurewerkz), [Michael](http://twitter.com/michaelklishin) and [Alex](http://twitter.com/ifesdjeen)
on Twitter.

Happy New Year!
