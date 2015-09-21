---
layout: post
title: "Neocons 3.1.0 is released"
date: 2015-09-22 02:04:25 +0300
comments: false
categories:
  - neocons
  - releases
---

## TL;DR

Neocons is a feature rich idiomatic [Clojure client for the Neo4J REST API](http://clojureneo4j.info).

`3.1.0` is a minor release that targets Neo4J server 2.2.


## Changes between Neocons 3.0.0 and 3.1.0

### Neo4J 2.2: Ability to Change Password

`clojurewerkz.neocons.rest.password/change-password` is a new function that
can be used to update user credentials:

``` clojure
(require 'clojurewerkz.neocons.rest.password :as pwd)

(pwd/change-password uri "joe" "old-pwd" "new-pwd")
```

Contributed by Rohit Aggarwal.


### Urly Dependency Dropped

Neocons no longer depends on Urly, a deprecated ClojureWerkz library.

Contributed by Ricardo J. Mendez.

### Clojure 1.7

Neocons now depends on `org.clojure/clojure` version `1.7.0`. It is
still compatible with Clojure 1.5 and if your `project.clj` depends on
a different version, it will be used, but 1.7 is the default now.

### clj-http Upgrade

clj-http dependency has been updated to `2.0.0`.

### Cheshire Upgrade

Cheshire dependency has been updated to `5.5.0`.

### HTTP Authentication via URI

It is now possible to specify credentials in the URI.

Contributed by Øystein Jakobsen.

### ClojureWerkz Support Upgrade

Neocons now uses ClojureWerkz Support 1.1.0.


## Change Log

[Neocons change log](https://github.com/michaelklishin/neocons/blob/master/ChangeLog.md)
is available on GitHub.


## Neocons is a ClojureWerkz Project

[Neocons](http://clojureneo4j.info) is part of the [group of libraries
known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Cassaforte](http://clojurecassandra.info), a Cassandra client built around CQL 3
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Neocons, you may also like [our other
projects](http://clojurewerkz.org).

Let us know what you think [on
Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing
list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the
[ClojureWerkz](http://clojurewerkz.org) Team
