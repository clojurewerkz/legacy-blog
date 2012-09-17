---
layout: post
title: "Quartzite 1.0"
date: 2012-09-18 00:22
comments: false
categories:
  - releases
  - quartzite
---

[Quartzite](http://clojurequartz.info) is a Clojure DSL on top of the Quartz scheduler. It has a few convenience features
in addition, but primarily tries to make core Quartz features as easy to use as possible without heavy use of Java interop in your apps.

Here's a list of what you get out of the box:

 * Ability to define jobs, triggers and schedules using a DSL
 * Scheduling, unscheduling, pausing and resuming jobs and triggers.
 * Querying scheduler for information, convenient predicate functions
 * Ability to register listeners for scheduler events
 * Access to durable scheduler data stores (JDBC databases out of the box, other stores via plugins)
 * Decent documentation (my favorite feature)


Quartzite targets Clojure 1.3+, tested against 3 Clojure versions x 3 JDKs on travis-ci.org, and is released under the Eclipse Public License.

Learn more in the [Getting Started guide](http://clojurequartz.info/articles/getting_started.html) and the rest of [the docs](http://clojurequartz.info/).

The source is available [on GitHub](http://github.com/michaelklishin/quartzite). We also use GitHub to track issues.


The [ClojureWerkz](http://clojurewerkz.org) Team
