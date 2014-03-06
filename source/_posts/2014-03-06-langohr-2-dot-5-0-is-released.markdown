---
layout: post
title: "Langohr 2.5.0 is released"
date: 2014-03-06 14:53:26 +0400
comments: false
categories:
  - langohr
  - releases
---

## TL;DR

Langohr is a small [Clojure RabbitMQ client](http://clojurerabbitmq.info).

`2.5.0` is a minor feature release that also deprecates several
functions.


## Changes between Langohr 2.3.x and 2.5.0

### langohr.http/declare-user Renamed

`langohr.http/declare-user` was renamed to `langohr.http/set-user`.

### langohr.http/declare-policy Renamed

`langohr.http/declare-policy` was renamed to `langohr.http/set-policy`.

### langohr.http/declare-permissions Renamed

`langohr.http/declare-permissions` was renamed to `langohr.http/set-permissions`.

### langohr.http/declare-user Renamed

`langohr.http/declare-user` was renamed to `langohr.http/add-user`.

### langohr.http/vhost-exists?

`langohr.http/vhost-exists?` is a new function that returns true if provided
vhost exists:

``` clojure
(require '[langohr.http :as hc])

(hc/vhost-exists? "killer-app-dev")
```

### langohr.http/user-exists?

`langohr.http/user-exists?` is a new function that returns true if provided
user exists:

``` clojure
(require '[langohr.http :as hc])

(hc/user-exists? "monitoring")
```

### RabbitMQ Java Client Upgrade

RabbitMQ Java client dependency has been updated to `3.2.4`.

### clj-http Upgrade

clj-http dependency has been updated to `0.7.9`.

### Topology Recovery Default

`:automatically-recover-topology` default is now `true`, as listed in
documentation.

Contributed by Ilya Ivanov.

### Deprecations

`langohr.core/automatically-recover?` is deprecated

Use `langohr.core/automatic-recovery-enabled?` instead.



## Change Log

[Langohr change
log](https://github.com/michaelklishin/langohr/blob/2.3.x-stable/ChangeLog.md)
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
