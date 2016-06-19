---
layout: post
title: "metrics-clojure 2.7.0 is released"
date: 2016-06-02 03:32:25 +0300
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


## Changes Between 2.6.0 and 2.7.0

### Functions for Working with Reservoirs

Ning Sun contributed several new functions that instantiate
various reservoir types:

 * `metrics.core/uniform-reservior`
 * `metrics.core/exponentially-decaying-reservoir`
 * `metrics.core/sliding-time-window-reservoir`
 * `metrics.core/sliding-window-reservoir`

and a few more.

GH issue: [#104](https://github.com/sjl/metrics-clojure/pull/104)

### Easier to Retrieve Metrics

Ning Sun contributed several new functions that retrieve different
type of metrics from a registry:

 * `metrics.core/meters`
 * `metrics.core/histograms`
 * `metrics.core/timers`
 * `metrics.core/gauges`
 * `metrics.core/counters`

GH issue: [#102](https://github.com/sjl/metrics-clojure/pull/102)

### Updated Dependencies

Contributed by Pierre-Yves Ritschard.



## Full Change Log

[metrics-clojure change log](https://github.com/sjl/metrics-clojure/blob/master/ChangeLog.md) is available on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [metrics-clojure](https://github.com/sjl/metrics-clojure) Team.

