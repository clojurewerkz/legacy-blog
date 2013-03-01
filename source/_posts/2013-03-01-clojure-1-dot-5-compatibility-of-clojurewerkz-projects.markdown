---
layout: post
title: "Clojure 1.5 Compatibility of ClojureWerkz Projects"
date: 2013-03-01 20:24
comments: false
categories: 
  - compatibility
---

## TL;DR

Clojure 1.5 is finally released. ClojureWerkz projects are compatible with it.
It's probably sunny outside, too.

Feel free to upgrade today!

## Clojure 1.5 and ClojureWerkz

Clojure 1.5 is finally [releases](https://groups.google.com/forum/?fromgroups=#!topic/clojure/kzF5O0Yfdhc).
While not a groundbreaking release, 1.5 brings more new features than 1.4 did. So, it's natural to expect
that many developers will consider upgrading to it soon.

One of the main goals of ClojureWerkz has always been making sure our libraries work with multiple Clojure
versions (currently 1.3+). To hold to the promise, we run tests against multiple Clojure versions
during development and on [travis-ci.org](http://travis-ci.org).
One of the versions is the master Clojure snapshot.

Starting with `1.5.0-RC*` releases, we started testing several of our projects against it:

 * [Monger](http://clojuremongodb.info)
 * [Elastisch](http://clojureelasticsearch.info)
 * [Langohr](http://clojurerabbitmq.info)
 * [Neocons](http://clojureneo4j.info)
 * [Welle](http://clojureriak.info)
 * [Titanium](http://titanium.clojurewerkz.org)
 * [Quartzite](http://clojurequartz.info)
 * [Urly](https://travis-ci.org/michaelklishin/urly)
 * [Support](https://travis-ci.org/clojurewerkz/support)

We are happy to report that none of those projects required any modifications to pass their
test suites on Clojure `1.5.0`.


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz Team](http://twitter.com/clojurewerkz).
