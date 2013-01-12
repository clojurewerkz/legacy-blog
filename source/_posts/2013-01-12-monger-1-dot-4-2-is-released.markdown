---
layout: post
title: "Monger 1.4.2 is released"
date: 2013-01-12 22:24
comments: false
categories: 
  - releases
  - monger
---

Monger is an idiomatic Clojure MongoDB driver for a more civilized age.
It has batteries included, offers powerful expressive query DSL, strives
to support every MongoDB 2.0+ feature and has sane defaults.
It also has solid documentation at http://clojuremongodb.info.

`1.4.2` is a minor *100% backwards-compatible* release that includes one bug fix.


## Changes between 1.4.1 and 1.4.2

### Explicit DBCursor Closure by monger.collection/find-maps and the like

`monger.collection/find-maps` and the like will now explicitly close DB cursors.

GH issue: [#47](https://github.com/michaelklishin/monger/pull/47)


## Changes between 1.4.0 and 1.4.1

### MongoDB Java Driver Update

MongoDB Java driver dependency [has been updated to 2.10.1](https://github.com/mongodb/mongo-java-driver/wiki/Release-Notes).



## Change Log

We recommend all users to upgrade to [1.4.2](https://clojars.org/com.novemberain/monger/versions/1.4.2) as soon as possible.
[Monger change log](https://github.com/michaelklishin/monger/blob/1.4.x-stable/ChangeLog.md) is available on GitHub.

[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz Team](http://twitter.com/clojurewerkz).
