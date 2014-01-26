---
layout: post
title: "Scrypt 1.1.0 is Released"
date: 2014-01-26 20:34:13 +0400
comments: false
categories:
  - scrypt
  - releases
---

## TL;DR

[ClojureWerkz Scrypt](https://github.com/clojurewerkz/scrypt) is a tiny Clojure library for working with [scrypt](http://www.tarsnap.com/scrypt/scrypt.pdf),
a key derivation function. Scrypt can be used to hash passwords and generate cryptographic
keys. It is an alternative to Bcrypt and PBKDF2.

Version 1.1.0 makes it possible to use a native scrypt implementation.


# Changes Between 1.0.0 and 1.1.0

## Lambdaworks Scrypt Upgrade

[Lambdaworks Scrypt](https://github.com/wg/scrypt) is updated to `1.4.0`,
which makes it possible to use a native implementation of the library.

To quote the docs:

```
The system property "com.lambdaworks.jni.loader" may be set to override
the default native library loader with one of the following values:

 * nil: refuse to load native libraries and revert to pure Java implementation
 * jar: extract native library from jar and load with System.load
 * sys: use System.loadLibrary, which may require java.library.path to be set
```

## Clojure 1.3 Support Dropped

Scrypt no longer officially supports Clojure 1.3.



## Scrypt is a ClojureWerkz Project

Scrypt is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Neocons](http://clojureneo4j.info), a Clojure client for the Neo4J REST API
 * [Cassaforte](http://clojurecassandra.info), a Clojure client for Cassandra built around CQL

and several others. If you like Scrypt, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz Team](http://twitter.com/clojurewerkz).
