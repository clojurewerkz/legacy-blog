---
layout: post
title: "Validateur 2.2.0 is released"
date: 2014-08-03 07:24:48 +0400
comments: false
categories:
  - validateur
  - releases
---

## TL;DR

[Validateur](http://clojurevalidations.info) is a functional validations library inspired by Ruby's ActiveModel.
Validateur 2.2 is a minor feature release.


## Changes Between 2.1.0 and 2.2.0

### nested

`nested` is a new validator runner for nested attributes.

``` clojure
(require '[validateur.validation :refer :all])

(let [v (vr/nested :user (vr/validation-set
                            (vr/presence-of :name)
                            (vr/presence-of :age)))
        extra-nested (vr/nested [:user :profile]
                                (vr/validation-set
                                 (vr/presence-of :age)
                                 (vr/presence-of [:birthday :year])))]
  (v {})
  ;= {[:user :age] #{"can't be blank"}
      [:user :name] #{"can't be blank"}}
  (v {:user {:name "name"}})
  ;= {[:user :age] #{"can't be blank"}}
  (extra-nested {:user {:profile {:age 10
                                  :birthday {:year 2004}}}})
  ;= {}
  (extra-nested {:user {:profile {:age 10}}})
  ;= {[:user :profile :birthday :year] #{"can't be blank"}}
```

Contributed by Sam Ritchie.

### validate-by

`validate-by` is a new validator function. It returns a function that,
when given a map, will validate that the + value of the attribute in
that map is one of the given:

``` clojure
(require '[validateur.validation :refer :all])

(validation-set
   (presence-of :name)
   (presence-of :age)
   (validate-by [:user :name] not-empty :message \"Username can't be empty!\"))
```

Contributed by Sam Ritchie.


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
