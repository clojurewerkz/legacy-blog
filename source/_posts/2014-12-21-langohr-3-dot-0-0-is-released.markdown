---
layout: post
title: "Langohr 3.0.0 is released"
date: 2014-12-21 19:57:44 +0300
comments: false
categories:
  - langohr
  - releases
---

## TL;DR

Langohr is a [Clojure RabbitMQ client](http://clojurerabbitmq.info) that embraces [AMQP 0.9.1 Model](http://www.rabbitmq.com/tutorials/amqp-concepts.html).

`3.0.0` is a major release that introduces breaking API changes, JDK 8
compatibility, minor new features and major internal revamp.


### Options as Maps

Functions that take options now require a proper Clojure map instead of
pseudo keyword arguments:

``` clojure
# in Langohr 2.x

(lq/declare ch q :durable true)
(lhcons/subscribe ch q (fn [_ _ _])
                        :consumer-tag ctag :handle-cancel-ok (fn [_]))
(lb/publish ch "" q "a message" :mandatory true)

# in Langohr 3.x
(lq/declare ch q {:durable true})
(lhcons/subscribe ch q (fn [_ _ _])
                        {:consumer-tag ctag :handle-cancel-ok (fn [_])})
(lb/publish ch "" q "a message" {:mandatory true})
```


### JDK 8 Compatibility

Langohr test suite now passes on JDK 8 (previously there was 1 failure
in recovery test).

GH issue: [#54](https://github.com/michaelklishin/langohr/issues/54).


### Connection Recovery Performed by Java Client

Langohr no longer implements automatic connection recovery
of its own. The feature is still there and there should be no
behaviour changes but the functionality has now been pushed
"upstream" in the Java client, so Langohr now relies on it
to do all the work.

There is two public API changes:

 * `com.novemberain.langohr.Recoverable` is gone, `langohr.core/on-recovery`
   now uses `com.rabbitmq.client.Recoverable` instead in its signature.

 * Server-named queues will change after recovery. Use `langohr.core/on-queue-recovery`
   to register a listener for queue name change.

GH issue: [#58](https://github.com/michaelklishin/langohr/issues/58).


### RabbitMQ Java Client Upgrade

RabbitMQ Java client dependency has been updated to `3.4.2`.

### Custom Exception Handlers

`langohr.core/exception-handler` is a function that customizes
default exception handler RabbitMQ Java client uses:

``` clojure
(require '[langohr.core :as rmq])

(let [(rmq/exception-handler :handle-consumer-exception-fn (fn [ch ex consumer
                                                               consumer-tag method-name]
                                                             ))]
  )
```

Valid keys are:

 * `:handle-connection-exception-fn`
 * `:handle-return-listener-exception-fn`
 * `:handle-flow-listener-exception-fn`
 * `:handle-confirm-listener-exception-fn`
 * `:handle-blocked-listener-exception-fn`
 * `:handle-consumer-exception-fn`
 * `:handle-connection-recovery-exception-fn`
 * `:handle-channel-recovery-exception-fn`
 * `:handle-topology-recovery-exception-fn`

GH issue: [#47](https://github.com/michaelklishin/langohr/issues/47).


### Clojure 1.7 Support

Clojure 1.7-specific compilation issues and warnings were eliminated.

### clj-http Upgrade

clj-http dependency has been updated to `1.0.0`.

### ClojureWerkz Support Upgrade

`clojurewerkz/support` dependency has been updated to `1.1.0`.


### langohr.core/version is Removed

`langohr.core/version` was removed.


## Change Log

[Langohr change log](https://github.com/michaelklishin/langohr/blob/master/ChangeLog.md)
is available on GitHub.


## Langohr is a ClojureWerkz Project

[Langohr](http://clojurerabbitmq.info) is part of the [group of
libraries known as ClojureWerkz](http://clojurewerkz.org), together
with

 * [Elastisch](http://clojureelasticsearch.info), a minimalistic well documented Clojure client for ElasticSearch
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client built around CQL 3.0
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Langohr, you may also like [our other
projects](http://clojurewerkz.org).

Let us know what you think [on
Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing
list](https://groups.google.com/group/clojure).


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the
[ClojureWerkz](http://clojurewerkz.org) Team
