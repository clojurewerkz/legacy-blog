---
layout: post
title: "metrics-clojure 2.5.0 is released"
date: 2015-03-29 18:47:28 +0300
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


## Changes Between 2.4.0 and 2.5.0

### Type Hints Use Fully-Qualified Names

Type hints across the libraries now use fully-qualified names, which means
returned types don't have to be imported in the caller namespaces.

Contributed by Jason Whitlark.

### :total Key In Timers

`metrics.timers/rate` return value now includes `:total`.

Contributed by Andrew Rudenko.


### Added remove-all-metrics function

`metrics-clojure` Now has a function to remove all existing metrics from a given registry.

Contributed by Jason Whitlark.


### Metrics 3.1.1

`metrics-clojure` is now based on [Metrics 3.1.1](https://github.com/dropwizard/metrics/issues/694#issuecomment-77668929).

Contributed by Jason Whitlark.


## Full Change Log

[metrics-clojure change log](https://github.com/sjl/metrics-clojure/blob/master/ChangeLog.md) is available on GitHub.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [metrics-clojure](https://github.com/sjl/metrics-clojure) Team.

