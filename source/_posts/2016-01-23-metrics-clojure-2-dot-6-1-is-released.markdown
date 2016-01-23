---
layout: post
title: "metrics-clojure 2.6.1 is released"
date: 2016-01-23 13:14:53 +0300
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


## Changes Between 2.6.0 and 2.6.1

### Dependencies Update

Contributed by Pierre-Yves Ritschard.


## Changes Between 2.5.0 and 2.6.0

### Riemann Reporter

Contribited by Ragnar Dahlén.

### DropWizard Metrics Upgrade

DropWizard Metrics was upgraded to `3.1.2`.

Contributed by Matthias Nüßler.

### Cheshire Upgrade

Cheshire was upgraded to `5.5.0`.

Contributed by Shantanu Kumar.

### Predicate-based Metric Removal

`metrics.core/remove-metrics` is a new function that removes
metrics based on a predicate.

Contributed by Vincent Bernat.

### Infinite Recursion in Ganglia

Ganglia reporter had an infinite recursion.

GH issue: #71.

### Add support for timing expressions in core.async/go blocks

Added the macro `metrics.timers/start-stop-time` to enable timing expressions that include parking functions in `core.async/go` blocks.

Contributed by Wil Yegelwel.



## Full Change Log

[metrics-clojure change log](https://github.com/sjl/metrics-clojure/blob/master/ChangeLog.md) is available on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [metrics-clojure](https://github.com/sjl/metrics-clojure) Team.

