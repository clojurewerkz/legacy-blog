---
layout: post
title: "Elastisch 1.3.0-beta2 is released"
date: 2013-09-02 21:20
comments: false
categories:
  - elastisch
  - releases
---



## TL;DR

Elastisch is a battle tested, small but feature rich and well documented [Clojure client for ElasticSearch](http://clojureelasticsearch.info).
It supports virtually every Elastic Search feature and has [solid documentation](http://clojureelasticsearch.info).

`1.3.0-beta2` is a development milestone release that is compatible with `1.2.0` except
for dropped Clojure 1.3 support.


## Changes between Elastisch 1.3.0-beta1 and 1.3.0-beta2

### Bulk Index and Delete Operations Support More Options

Bulk index and delete operations support `_parent` and `_routing`
keys.

Contributed by Baptiste Fontaine.

### Clojure 1.3 Support Dropped

Elastisch now requires Clojure 1.4.



## Changes between Elastisch 1.2.0 and 1.3.0-beta1

### Cheshire Update

[Cheshire](https://github.com/dakrone/cheshire/) dependency has been upgraded to version `5.2.0`.

### clj-http Update

[clj-http](https://github.com/dakrone/clj-http/) dependency has been upgraded to version `0.7.6`.


## Change log

[Elastisch change log](https://github.com/clojurewerkz/elastisch/blob/master/ChangeLog.md) is available on GitHub.


## Thank You, Contributors

Kudos to Baptiste Fontaine for contributing to this release.


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


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
