---
layout: post
title: "Validateur 2.0.0 is released"
date: 2014-04-02 18:11:51 +0400
comments: false
categories:
  - validateur
  - releases
---

## TL;DR

[Validateur](http://clojurevalidations.info) is a functional validations library inspired by Ruby's ActiveModel.
Validateur 2.0 is a feature release.


## Changes Between 1.7.0 and 2.0.0

### Clojure 1.6

Validateur now depends on `org.clojure/clojure` version `1.6.0`. It is
still compatible with Clojure 1.4 and if your `project.clj` depends on
a different version, it will be used, but 1.6 is the default now.


### Validator Predicates (Guards)

It is now possible to wrap a validator into a function
that will check a condition before applying the validator.

To do so, use `validate-when`:

``` clojure
(require '[validateur.validation])

(defn new?
  [user]
  (nil? (:id user)))

(defn unique-email?
  [user]
  (if-let [existing (find-by-email (:email user)]
    (= (:id user) (:id existing))
    true))

(def validate
  (validation-set
    (presence-of :email)
    (validate :email unique-email? :message "is already taken")
    (validate-when new? (presence-of :password))
    (validate-when #(contains? % :password) (presence-of :password))))
```

If provided predicate returns `false`, the validator it guards is not
executed.

[Contributed](https://github.com/michaelklishin/validateur/pull/23) by Scott Nelson.

### Generic Validator

Generic validator uses a predicate function and attaches errors to specified
attribute:

``` clojure
(require '[validateur.validation])

(validate-with-predicate :id unique? :message "ID is not unique")
```

[Contributed](https://github.com/michaelklishin/validateur/pull/23) by Scott Nelson.

### ClojureWerkz Support Dependency Dropped

ClojureWerkz Support is no longer a dependency of Validateur.
This makes it easier to use Validateur in ClojureScript projects.

Contributed by hura.

### Validation Set Composition

Validateur now supports composition of validation sets. To
compose several sets, use `validateur.validation/compose-sets`:

``` clojure
(let [vn (vr/validation-set
           (vr/presence-of :name))
      va (vr/validation-set
           (vr/presence-of :age))
      v  (vr/compose-sets va vn)]
  ;= true
  (vr/valid? v { :name "Joe" :age 28 }))
```

Contributed by hura.


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
