---
layout: post
title: "Carmine 2.0.0-beta1 is released"
date: 2013-06-26 22:45
comments: false
categories:
  - carmine
  - releases
---

## TL;DR

[Carmine](https://github.com/ptaoussanis/carmine) is fantastic Clojure client for Redis.

`2.0.0` is a major release that introduces some *breaking API changes*, new features
and another 20% performance improvement (now within less than 5% of the Java client).


## Changes in Carmine 2.0

 * 20% better performance
 * Pluggable data compression and encryption based on [Nippy 2.0](https://github.com/ptaoussanis/nippy)
 * Improvements to [message queueing](https://github.com/ptaoussanis/carmine#message-queue) and distributed locking features
 * [Tundra](https://github.com/ptaoussanis/carmine#tundra), a way to plug a durable data store into Carmine for long-term data persistence

(sorry that the change log is so concise. We've asked Peter to keep a slightly more detailed one!)


## Carmine 2.0 Migration Guide

Carmine users should get themselves familiar with the [Carmine 2.0 Migration Guide](https://github.com/ptaoussanis/carmine/blob/master/MIGRATION-v2.md)
before upgrading.


## Carmine Has Sister Projects

[Carmine](https://github.com/ptaoussanis/carmine) is part of the [group of libraries by Peter Taoussanis](https://www.taoensso.com/clojure-libraries), together with

 * [Timbre](https://github.com/ptaoussanis/timbre), a pure Clojure logging and profiling library
 * [Tower](https://github.com/ptaoussanis/touchstone), a Clojure library for split testing
 * [Nippy](https://github.com/ptaoussanis/nippy), a fast drop-in replacement for the Clojure reader
 * [Faraday](https://github.com/ptaoussanis/faraday), a Clojure DynamoDB client
 * [Touchstone](https://github.com/ptaoussanis/tower), a pure Clojure library for i18n and l10n

If you like these projects, you should [follow Peter on Twitter](http://twitter.com/ptaoussanis).


[@michaelklishin](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
