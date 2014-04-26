---
layout: post
title: "Validateur 2.1.0 is released"
date: 2014-04-27 00:58:04 +0400
comments: false
categories:
  - validateur
  - releases
---

## TL;DR

[Validateur](http://clojurevalidations.info) is a functional validations library inspired by Ruby's ActiveModel.
Validateur 2.1 is a minor feature release.


## Changes Between 2.0.0 and 2.1.0

### Multi-field Support For Presence Validator

`presence-of` validator now supports validation over
multiple (all or any) fields:

``` clojure
;; both fields must be non-nil
(vr/presence-of #{:name :msg})

;; either field must be non-nil
(vr/presence-of #{:name :msg} :any true)
```

Contributed by Radosław Piliszek.

### Better ClojureScript Support

Validateur no longer uses crossovers which are
deprecated in `lein-cljsbuild`.

Contributed by Radosław Piliszek.



## Full Change Log

[Validateur change log](https://github.com/michaelklishin/validateur/blob/master/ChangeLog.md) is available on GitHub.



## Validateur is a ClojureWerkz Project

[Validateur](http://github.com/michaelklishin/validateur) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client built around CQL
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Validateur, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).

## About The Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
