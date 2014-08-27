---
layout: post
title: "metrics-clojure 2.2.0 is released"
date: 2014-08-27 17:52:06 +0400
comments: false
categories:
  - metrics
  - releases
---

## TL;DR

[metrics-clojure](https://github.com/sjl/metrics-clojure/) is a Clojure façade around Coda Hale's [Metrics](http://metrics.codahale.com) library,
originally developed by [Steve Losh](http://stevelosh.com/).

`metrics-clojure` is not a ClojureWerkz project but we help maintain it
and consider it to be a very valuable library.


## Changes Between 2.1.x and 2.2.0

### Graphite Extension

`metrics.reporters.graphite` is a new sub-project that contains
a Graphite reporter.


### Ring Extension Now Respects User-provided Registry

The Ring extension now respects user-provided registries
instead of always using the default one.

Contributed by David Smith.

### Bugfixes

- Fixed `metrics.core/default-registry` to have a valid reflection
  hint (no longer causes compile error when used in interop.) Fix
  planned on 2.1.x as well. Contributed by Tim McCormack.


## Full Change Log

[metrics-clojure change log](https://github.com/sjl/metrics-clojure/blob/master/ChangeLog.md) is available on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [metrics-clojure](https://github.com/sjl/metrics-clojure) Team.

