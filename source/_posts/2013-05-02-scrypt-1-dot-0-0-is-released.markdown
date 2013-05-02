---
layout: post
title: "Scrypt 1.0.0 is released"
date: 2013-05-02 09:00
comments: false
categories:
  - scrypt
  - releases
---

## TL;DR

[ClojureWerkz Scrypt](https://github.com/clojurewerkz/scrypt) is a tiny Clojure library for working with [scrypt](http://www.tarsnap.com/scrypt/scrypt.pdf),
a key derivation function. Scrypt can be used to hash passwords and generate cryptographic
keys. It is an alternative to Bcrypt and PBKDF2.


## Why Use Scrypt

Values (e.g. passwords) encrypted with Scrypt are much more computationally hard to crack than with most other
available key derivation functions:

![Key Derivation Function Comparison](/images/posts/kdf-comparison.png)

More can be found in the [scrypt paper](http://www.tarsnap.com/scrypt/scrypt.pdf).


## What's In The Box

Scrypt is literally a couple of functions:

 * Encrypt a value (e.g. a password)
 * Verify a candidate against a hash (e.g. against a password used to authenticate)


## Documentation

Scrypt is a small library and all of its [documentation guide fits in the README](https://github.com/clojurewerkz/scrypt#documentation).


## Supported Clojure Versions

Scrypt supports Clojure 1.3+.



## News and Updates

New releases and updates are announced [on Twitter](http://twitter.com/clojurewerkz).


## Scrypt is a ClojureWerkz Project

Scrypt is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Titanium](http://titanium.clojurewerkz.org), a powerful graph library built on top of [Titan](http://thinkaurelius.github.io/titan/)
 * [Neocons](http://clojureneo4j.info), a Clojure client for the Neo4J REST API
 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Scrypt, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz Team](http://twitter.com/clojurewerkz).
