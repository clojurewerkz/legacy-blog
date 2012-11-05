---
layout: post
title: "Carmine, Timbre, Tower, and Nippy go 1.0"
date: 2012-11-05 23:41
comments: false
categories: 
categories: 
  - releases
---

## TL;DR

A bunch of awesome libraries from our friend [Peter Taoussanis](https://www.taoensso.com/) went 1.0
recently. You should check them out [on GitHub](https://github.com/ptaoussanis).


## 1.0 Releases Galore

We at ClojureWerkz have been fans of [Peter Taoussanis](https://www.taoensso.com/) for a while. So much so,
some of his libraries are listed on our [home page](http://clojurewerkz.org), even though they are not
projects we maintain. Recently 4 of them went 1.0 and we would like to cover them briefly.


## Carmine 1.0

[Carmine](https://github.com/ptaoussanis/carmine) is an awesome Clojure client for Redis. And we don't call libraries
awesome for no reason: it supports nearly all Redis 2.6+ features, well maintained, supports multiple Clojure versions,
has a very good performance baseline.

[Carmine documentation](https://github.com/ptaoussanis/carmine/blob/master/README.md) is much better than
the average open source project and written with beginners in mind.

Carmine is not a young project: Peter has been working on it for a while. Version after version, month after month,
the library has gotten to the point when it really can be labelled 1.0.

The project is licensed under the [Eclipse Public License](http://www.eclipse.org/legal/epl-v10.html) and [tested against 3 Clojure versions + 3 JDKs](http://travis-ci.org/ptaoussanis/carmine).

If you are looking for a [Clojure Redis client](https://github.com/ptaoussanis/carmine), look no further than Carmine.


## Tower 1.0

[Tower](https://github.com/ptaoussanis/tower) is an internationalization (i18n) library for Clojure. Tower wraps JDK localization features where appropriate,
adds map-based translation dictionary format, supports REPL-friendly dictionary reloading, Markdown support and [Ring](https://github.com/ring-clojure/ring) middleware.

The project is licensed under the [Eclipse Public License](http://www.eclipse.org/legal/epl-v10.html) and [tested against 3 Clojure versions + 3 JDKs](http://travis-ci.org/ptaoussanis/tower).

Usage examples can be found in the [README](https://github.com/ptaoussanis/tower/blob/master/README.md).


## Timbre 1.0

Timbre is a pure Clojure, no-XML and no-bullshit logging library. If you never found existing JVM logging tools
and `tools.logging` appealing or easy to use, try Timbre. Timbre appenders are Clojure functions, the library
is extensible, supports asynchronous logging and flood control.

Sounds like a sweet [Clojure logging library](https://github.com/ptaoussanis/timbre) to us!


## Nippy 1.0

In Clojure, code is data and to support it, the reader (parser) is exposed to the language itself and can be extended.
There is one downside, however: the built-in reader is not particularly efficient (it was built for compile time operation).

[Nippy](https://github.com/ptaoussanis/nippy) provides an alternative implementation of the Clojure reader that is much more efficient.

For Clojure-to-Clojure messaging, Nippy may be one of the most interesting serialization libraries available today.


## Wrapping Up

Great work, Peter! Carmine, Tower, Timbre and Nippy are all examples of well maintained open source projects.
Bonus points for covering practical areas (data stores, i18n, logging), attention to compatibility with multiple
Clojure versions and newcomer-friendly documentation.

These are examples the Clojure community needs to follow.

