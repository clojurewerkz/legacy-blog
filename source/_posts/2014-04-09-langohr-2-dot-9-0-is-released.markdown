---
layout: post
title: "Langohr 2.9.0 is released"
date: 2014-04-09 14:36:19 +0400
comments: false
categories:
  - langohr
  - releases
---

## TL;DR

Langohr is a small [Clojure RabbitMQ client](http://clojurerabbitmq.info).

`2.9.0` is a minor feature release.


## Changes between Langohr 2.8.x and 2.9.0

### Configurable Default and Per-Operation Options in HTTP API Client

Most HTTP API client functions now have an additional optional arguments,
which is a map of options passed to `clj-http` functions. This lets you fine
tune certain HTTP requests as needed.

In addition, `langohr.http/connect!` now accepts one more argument which serves
as default HTTP client options merged with the options provided per `langohr.http`
function call:

``` clojure
(require '[langohr.http :as hc])

;; non-20x/30x statuses will now throw exceptions
(hc/connect! "http://127.0.0.1:15673" "guest" "guest" {:throw-exceptions true})

;; disable throwing exceptions for an individual operation,
;; because 404 is an expected HTTP response in this case
(hc/vhost-exists? "myapp-production" {:throw-exceptions false})
;= false

;; disabling peer verification for HTTPS requests
(hc/connect! "http://127.0.0.1:15673" "guest" "guest" {:insecure? true})
```

### Thread Factory Customization

It is now possible to customize a `java.util.concurrent.ThreadFactory`
used by Langohr connections. The factory will be used to instantiate
all threads created by the client under the hood.

The primary use case for this is running on Google App Engine which
prohibits direct thread instantiation and requires apps to use 
thread manager (or thread factory) from GAE SDK instead.

To provide a custom thread factory, pass it as `:thread-factory` to
`langohr.core/connect`. To reify a thread factory with a Clojure function,
use `langohr.core/thread-factory-from`:

``` clojure
(require '[langohr.core :as lc])

(let [tf (lc/thread-factory-from
            (fn [^Runnable r]
              (Thread. r)))]
  (lc/connect {:thread-factory tf}))
```

### com.rabbitmq.client.TopologyRecoveryException is Used

Langohr now uses com.rabbitmq.client.TopologyRecoveryException instead of
reinventing its own exception to indicate topology recovery failure.

### RabbitMQ Java Client Compatibility

A few RabbitMQ Java client interface compatibility issues are resolved.


## Change Log

[Langohr change
log](https://github.com/michaelklishin/langohr/blob/master/ChangeLog.md)
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

## About The Author

[Michael](http://twitter.com/michaelklishin) on behalf of the
[ClojureWerkz](http://clojurewerkz.org) Team
