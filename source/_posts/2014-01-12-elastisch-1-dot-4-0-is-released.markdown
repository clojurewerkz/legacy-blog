---
layout: post
title: "Elastisch 1.4.0 is released"
date: 2014-01-12 13:46
comments: false
categories:
  - elastisch
  - elasticsearch
  - releases
---

## TL;DR

Elastisch is a battle tested, small but feature rich and well documented [Clojure client for ElasticSearch](http://clojureelasticsearch.info).
It supports virtually every Elastic Search feature and has [solid documentation](http://clojureelasticsearch.info).

[1.4.0](https://clojars.org/clojurewerkz/elastisch/versions/1.3.0) is a minor feature and usability release. We recommend all users to upgrade to it.


## Changes between Elastisch 1.3.0 and 1.4.0

### Native Document Supports Optimistic Locking

The native document API now supports the same :version option for optimistic
locking that the REST api does.

Contributed by Richie Vos (Groupon).

GH issues: #56.

### ElasticSearch Exceptions

Elastisch now uses ElasticSearch exceptions instead of generic ones in the native
client.

Contributed by Richie Vos (Groupon).

GH issues: #54, #57.

### ElasticSearch Native Client Upgrade

Elastisch now depends on ElasticSearch native client version `0.90.8`.

### `clojurewerkz.elastisch.native.document/update-with-script` Fix

`clojurewerkz.elastisch.native.document/update-with-script` invoked without
script parameters no longer raises an exception.


### Cheshire Upgrade

Cheshire dependency has been updated to `5.3.1`.


[Elastisch change log](https://github.com/clojurewerkz/elastisch/blob/1.4.x-stable/ChangeLog.md) is available on GitHub.


## Thank You, Contributors

Kudos to Richie Vos for contributing to this release.


## Elastisch is a ClojureWerkz Project

[Elastisch](http://clojureelasticsearch.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client
 * [Titanium](http://titanium.clojurewerkz.org), a Clojure graph library
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Elastisch, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
