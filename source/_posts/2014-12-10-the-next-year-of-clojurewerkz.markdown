---
layout: post
title: "The next year of ClojureWerkz"
date: 2014-12-10 21:20:37 +0300
comments: false
categories:
  - misc
---

## 3 Years Old

ClojureWerkz has turned 3 last November. This is an age for an open source
project at which the dust from initial development has begun to settle.

In this post we'd like to briefly outline what our plans are for the next year with ClojureWerkz.


## Where We Are Today

We have close to 40 projects total (a few of them are now defunct, about 5 are incubating and not yet
ready to be announced, some 30 have been around and used in production for at least half a year.

Our projects cover boring problems most developers face at some point:

 * Working with data stores
 * Working with message brokers (queues)
 * Data validation
 * Scheduling
 * Key derivation (stronger hashing)
 * Asynchronous and concurrent programming
 * Web crawling

We've also contributed to quite a few of our dependencies and related libraries, as well as [clojure-doc.org](http://clojure-doc.org),
a community-developed set of Clojure documentation guides.

We've been true to our values:

 * Solving boring problems.
 * No bullshit, easy contribution process that includes people from all over the world.
 * Solid documentation.
 * Sane APIs.

which I'm personally quite fond of.

## The Most Exciting Change

The most exciting change by far is that several of our projects now have [co-]maintainers outside of the
original ClojureWerkz team. Neocons, Titanium, Ogre, Archimedes are now driven by folks who've joined
us in the last year. Elastisch, Cassaforte, Validateur all have contributors
that are active every month (if not every week).

Making it easy to join a project is incredibly important for the project's sustainability. We are
making progress on that end.


## What's Ahead

As the number of projects and users grows, we have to keep things more predictable. Changes that are
likely to affect more users should be announced upfront and for all projects. A few of such changes
have been considered before and now it's time to begin implementing them:

 * Drop Clojure 1.4 and 1.5 support.
 * Drop JDK 6 support.
 * Dual-license projects under the Eclipse Public License 1.0 and Apache Software License 2.0, where possible.
 * Introduce a scale of project maturity.

Most of these are fairly self-explanatory but we'll post more about them in upcoming weeks.


## Helping You Help Us

Another thing that we've learnt over the last few years is: there are awesome people out there
who would come out of the blue with contributions if original project authors make it easy.

We've been trying to make it easy, namely

 * We don't require a contributor agreement
 * We accept pull requests on GitHub instead of asking for patches in a bottle
 * We try to make it easy to discover how to set up a test environment and run project tests
 * We use a hosted CI service

However, there's one thing where we have a lot of work to do: making it easy to discover **what to work on**.

In upcoming weeks we are going through issue trackers of all of our actively developed projects and tagging
issues suitable for beginners with "Low hanging fruit". Leiningen has been doing this for a long time
and it works well (they have 241 contributor at the time of writing, for science's sake!).

We'll also try to pipe some of those low hanging fruit issues into [Clojure in the Open](http://www.longstorm.org/weekly/cito/1/),
an awesome initiative by Vic Goldfeld.


## Legal Entity for ClojureWerkz

We are considering setting up a legal entity to make it easy to donate to ClojureWerkz and take
us to the next level. Having such entity is going to take a lot of work but also going to
open a lot of doors for us. If you have experience with setting up foundations in the UK
or EU and would like to help, please [contact us](mailto:michael@clojurewerkz.org).


## Wrapping Up

ClojureWerkz is growing. We're still not attracted by esoteric problems, so you can expect more of what we've
been doing all this time. It will be easier to help us.

[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team.
