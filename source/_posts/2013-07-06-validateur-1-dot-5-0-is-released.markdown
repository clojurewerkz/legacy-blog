---
layout: post
title: "Validateur 1.5.0 is released"
date: 2013-07-06 23:35
comments: false
categories:
  - validateur
  - releases
---

## TL;DR

[Validateur](http://clojurevalidations.info) is a functional validations library inspired by Ruby's ActiveModel.
Validateur 1.5 introduces ways to customize error messages.


## Changes between Validateur 1.4.0 and 1.5.0

### Optional messages in built-in validators

All built-in validators but length-of accept optional messages for all
cases. Their formatting is fixed and based in default ones.
For example:

``` clojure
((inclusion-of :genre :in #{"trance", "dnb"} :message "debe pertenecer a:")
 {:genre "pasodoble"})
;; [false {:genre #{"debe pertenecer a: trance, dnb"}}]
```

### Optional function callback to parametrize the construction of messages

All built-in validators accept an optional function callback which
will be called by the validator to build the returned error message.
The main goal is to facilitate the inclusion of i18n in messages (like
previous one but in a more flexible way).
For example:

``` clojure
((inclusion-of :genre :in #{"trance", "dnb"}
               :message-fn (fn [validator map prop & args]
                              [validator map prop args]))
 {:genre "pasodoble"})
;; [false {:genre #{[:inclusion {:genre "pasodoble"} :genre (#{"trance" "dnb"})]}}]
```



## Change Log

We recommend all users to upgrade to [1.5.0](https://clojars.org/com.novemberain/validateur/versions/1.5.0).

[Validateur change log](https://github.com/michaelklishin/validateur/blob/master/ChangeLog.md) is available on GitHub.


## Thank You, Contributors

Javier Neira contributed key features in this release.



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


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
