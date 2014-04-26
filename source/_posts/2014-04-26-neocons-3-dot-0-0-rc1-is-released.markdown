---
layout: post
title: "Neocons 3.0.0-rc1 is released"
date: 2014-04-26 19:18:08 +0400
comments: false
categories:
  - neocons
  - releases
---

## TL;DR

Neocons is a feature rich idiomatic [Clojure client for the Neo4J REST API](http://clojureneo4j.info).

`3.0.0-rc1` is a release candidate.  It has **one major breaking API change**
compared to `2.0.x`: every function now takes a connection record as
an explicit argument instead of relying on a dynamic var.


## Changes between Neocons 2.0.0 and 3.0.0

### Breaking Change: Explicit Connection Argument

Neocons no longer uses a dynamic var to hold the state of the connection.
This leads to significant changes to the API as the connection has to be
passed to functions. The position of the connection argument is always the
first argument for the sake of consistency:

``` clojure
(require '[clojurewerkz.neocons.rest :as nr])
(require '[clojurewerkz.neocons.rest.nodes :as nn])

;; with Neocons 2.0

(nr/connect! "http://localhost:7476/db")
(nn/create {:url "http://clojurewerkz.org/"})

;; with Neocons 3.0
(let [conn (nr/connect "http://localhost:7476/db")]
  (nn/create conn {:url "http://clojurewerkz.org/"}))
```

Additionally `connect!` function in `clojurewerkz.neocons.rest` no longer
exists. This has been replaced by function `connect` in `clojurewerkz.neocons.rest`.
The `connect` function has the same arguments as the `connect!` function
only it returns a `Connection` record.

The `Connection` record has a key called `:options` which can be used to pass
additional parameters to be used by [clj-http](https://github.com/dakrone/clj-http)
like `debug`.

Contributed by Rohit Aggarwal.


### Clojure 1.6

Neocons now depends on `org.clojure/clojure` version `1.6.0`. It is
still compatible with Clojure 1.4 and if your `project.clj` depends on
a different version, it will be used, but 1.6 is the default now.

### Cheshire 5.3

Neocons now uses [Cheshire](https://github.com/dakrone/cheshire) 5.3.

### clj-http upgraded to 0.9.1

Neocons now uses clj-http 0.9.1.

### Neo4J 2.0 Index Creation Fix

Neocons will now use a key name accepted by Neo4J 2.0.0 GA
and later version when creating indexes.

Contributed by Rohit Aggarwal.


## Change Log

We encourage all users to give this version a try.

[Neocons change
log](https://github.com/michaelklishin/neocons/blob/master/ChangeLog.md)
is available on GitHub.


## Documentation Updates

[Neocons documentation](http://clojureneo4j.info) has been updated to cover the new API.


## Thank You, Contributors

We'd like to thank [Rohit Aggarwal](https://github.com/ducky427) for
single-handedly doing all the work in Neocons 3.0. Contributors
like Rohit is why open source software works as well as it does.


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
