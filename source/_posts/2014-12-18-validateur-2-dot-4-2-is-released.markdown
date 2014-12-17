---
layout: post
title: "Validateur 2.4.2 is released"
date: 2014-12-18 02:01:08 +0300
comments: false
categories:
  - validateur
  - releases
---

## TL;DR

[Validateur](http://clojurevalidations.info) is a functional validations library inspired by Ruby's ActiveModel.
Validateur 2.4 is a minor feature release.


## Changes Between 2.3.0 and 2.4.0

### Clojure 1.4 Support Dropped

The project no longer tries to maintain Clojure 1.4 compatibility.

### validate-some

`validate-some` tries any number of validators, short-circuiting at the first failed validator. This behavior is similar to `or`.

```clojure
(require '[validateur.validation :refer :all])

(let [v (validate-some
         (presence-of :cake-count :message "missing_cake")
         (validate-by :cake-count odd? :message "even_cake"))]

  "Odd cake counts are valid."
  (v {:cake-count 1})
  ;;=> [true #{}]


  "Even cake counts only throw the second error, since the first
  validation passed."
  (v {:cake-count 2})
  ;;=> [false {:cake-count #{"even_cake"}}]

  "The second validation never gets called and never throws a NPE, as
  it would if we just composed them up."
  (v {})
  ;;=> [false {:cake-count #{"missing_cake"}}]
  )
```

Contributed by Sam Ritchie (PaddleGuru).

### errors? and errors

Errors in validateur are vectors if keys are nested. If keys are only
one layer deep - `:cake`, for example - the error can live at `:cake`
or `[:cake]`.

The `errors` function returns the set of errors for some key, nested
or bare. `:cake` will return errors stored under `[:cake]` and
vice-versa.

`errors?` is a boolean wrapper that returns true if some key has
errors, false otherwise.

Contributed by Sam Ritchie (PaddleGuru).



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
