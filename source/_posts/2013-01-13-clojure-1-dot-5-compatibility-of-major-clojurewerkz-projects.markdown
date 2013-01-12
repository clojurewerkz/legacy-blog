---
layout: post
title: "Clojure 1.5 Compatibility of Major ClojureWerkz Projects"
date: 2013-01-13 00:10
comments: false
categories:
  - compatibility
---

## TL;DR

Clojure 1.5 is around the corner. ClojureWerkz projects are compatible with it.
It's probably sunny outside, too.

Feel free to upgrade today!

## Clojure 1.5 and ClojureWerkz

Clojure 1.5 is [around the corner](https://groups.google.com/forum/?fromgroups=#!topic/clojure/CAiajyDWJJg).
While not a groundbreaking release, 1.5 brings more new features than 1.4 did. So, it's natural to expect
that many developers will consider upgrading to it soon.

One of the main goals of ClojureWerkz has always been making sure our libraries work with multiple Clojure
versions (currently 1.3+). To hold to the promise, we run CI against multiple Clojure versions
on [travis-ci.org](http://travis-ci.org). One of the versions is the master Clojure snapshot.

After the `1.5.0-RC1` release, we started testing several of our projects against it:

 * [Monger](https://travis-ci.org/michaelklishin/monger)
 * [Elastisch](https://travis-ci.org/clojurewerkz/elastisch)
 * [Langohr](https://travis-ci.org/michaelklishin/langohr)
 * [Neocons](https://travis-ci.org/michaelklishin/neocons)
 * [Welle](https://travis-ci.org/michaelklishin/welle)
 * [Quartzite](https://travis-ci.org/michaelklishin/quartzite)
 * [Support](https://travis-ci.org/clojurewerkz/support)

We are happy to report that none of those projects required any modifications to pass their
test suites on Clojure `1.5.0-RC1`.


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz Team](http://twitter.com/clojurewerkz).
