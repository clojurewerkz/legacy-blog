---
layout: post
title: "metrics-clojure 2.3.0 is released"
date: 2014-09-13 23:48:35 +0400
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


## Changes Between 2.2.x and 2.3.0

### Enhanced Timers

`metrics.timers` now provides two new functions, `start` and `stop`.

Contributed by Jason Whitlark.

### metrics.health

`metrics-clojure-health` is a new sub-project that makes implementing
[health checks](http://metrics.codahale.com/manual/healthchecks/) easier in Clojure.

Contributed by Jason Whitlark.

### Ganglia Reporter

`metrics-clojure-ganglia` is a new sub-project that makes using the Ganglia
reporter easier from Clojure.

Contributed by Jason Whitlark.

### CSV Reporter

CSV reporter is now provided in `metrics.reporters.csv`.

Contributed by Jason Whitlark.

### JMX Reporter

JMX reporter is now provided in `metrics.reporters.jmx`.

Contributed by Jason Whitlark.

### Stop Function for Reporter

All reporter namespace now provide a new function, `stop`, that stops
their respective reporter.

Contributed by Jason Whitlark.

### Graphite Reporter API in Line With the Console One

`metrics.reporters.graphite/start` is a function that starts the reporter,
just like other reporter namespaces (e.g. console) do.

Contributed by Jason Whitlark.

### Graphite and Console Reporters Documentation Improvements

Contributed by Jason Whitlark.


## Thank You, Contributors

We'd like to thank Jason Whitlark for contributing pretty much everything there
is in the `2.3.0` release.


## Full Change Log

[metrics-clojure change log](https://github.com/sjl/metrics-clojure/blob/master/ChangeLog.md) is available on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [metrics-clojure](https://github.com/sjl/metrics-clojure) Team.

