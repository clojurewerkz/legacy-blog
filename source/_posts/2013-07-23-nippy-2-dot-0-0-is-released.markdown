---
layout: post
title: "Nippy 2.0.0 is released"
date: 2013-07-23 22:28
comments: false
categories:
  - nippy
  - releases
---

## TL;DR

[Nippy](https://github.com/ptaoussanis/nippy) is an attempt to provide a reliable, high-performance drop-in alternative to the Clojure reader.

`2.0.0` is a major *completely backwards-compatible* release that includes several
new features.


## Changes in Nippy 2.0

Nippy 2.0 is a *backwards-compatible* release that introduces several new features:

  * **MIGRATION NOTE**: Please be sure to use `lein clean` to clear old (v1) build artifacts!
  * Refactored for huge performance improvements (~40% roundtrip time).
  * New header format for better error messages.
  * New `taoensso.nippy.tools` ns for easier integration with 3rd-party tools.

  * **DEPRECATED**: `freeze-to-bytes` -> `freeze`, `thaw-from-bytes` -> `thaw`.
    See the new fn docstrings for updated opts, etc.

  * Added pluggable compression support:

    ```clojure
    (freeze "Hello") ; defaults to:
    (freeze "Hello" {:compressor taoensso.nippy.compression/snappy-compressor})

    ;; The :compressor value above can be replaced with nil (no compressor) or
    ;; an alternative Compressor implementing the appropriate protocol
    ```

  * Added pluggable crypto support:

    ```clojure
    (freeze "Hello") ; defaults to:
    (freeze "Hello" {:encryptor taoensso.nippy.encryption/aes128-encryptor}

    ;; The :encryptor value above can be replaced with nil (no encryptor) or
    ;; an alternative Encryptor implementing the appropriate protocol
    ```

    See the [README](https://github.com/ptaoussanis/nippy#encryption-currently-in-alpha) for an example using encryption.



## Nippy Has Sister Projects

[Nippy](https://github.com/ptaoussanis/nippy) is part of the [group of libraries by Peter Taoussanis](https://www.taoensso.com/clojure-libraries), together with

 * [Carmine](https://github.com/ptaoussanis/carmine), a fantastic Clojure client for Redis
 * [Faraday](https://github.com/ptaoussanis/faraday), a Clojure DynamoDB client
 * [Timbre](https://github.com/ptaoussanis/timbre), a pure Clojure logging and profiling library
 * [Tower](https://github.com/ptaoussanis/touchstone), a Clojure library for split testing
 * [Touchstone](https://github.com/ptaoussanis/tower), a pure Clojure library for i18n and l10n

If you like these projects, you should [follow Peter on Twitter](http://twitter.com/ptaoussanis).


[@michaelklishin](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
