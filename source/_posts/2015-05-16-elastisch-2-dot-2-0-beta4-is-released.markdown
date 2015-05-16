---
layout: post
title: "Elastisch 2.2.0-beta4 is released"
date: 2015-05-16 14:49:14 +0300
comments: false
categories:
  - elastisch
  - elasticsearch
  - releases
---

## TL;DR

Elastisch is a battle tested, small but feature rich and well
documented [Clojure client for ElasticSearch](http://clojureelasticsearch.info). It supports
virtually every Elastic Search feature and has [solid documentation](http://clojureelasticsearch.info).

[2.2.0-beta4](https://clojars.org/clojurewerkz/elastisch/versions/2.2.0-beta4) is a preview
release of Elastisch 2.2 which introduces minor improvements.


## Changes between Elastisch 2.2.0-beta3 and 2.2.0-beta4

### ElasticSearch Java Client Upgrade

Elastisch now depends on ElasticSearch Java client version `1.5.x`.

### clj-http Update

[clj-http](https://github.com/dakrone/clj-http/) dependency has been upgraded to version `1.1.x`.

### Better support for plural/single indices and aliases in native update-aliases

* `:remove` action now works with singular `:index` key 
* multiple aliases can be added with single `:add` action
* alias can be removed from multiple indices with single `:remove` action

Contributed by @mnylen

### Index Settings Now Allow Keywordized Keys When Creating Index Using Native API

Previously only mappings allowed keys to be keywords, now same works with index settings.

Contributed by @mnylen

## Changes between Elastisch 2.2.0-beta2 and 2.2.0-beta3

### Support for Large Scroll IDs

Elastisch now supports scroll IDs larger than 4 KB.


Contributed by niko.


## Changes between Elastisch 2.2.0-beta1 and 2.2.0-beta2

### Bulk Operation Support in Native Client

Native client now supports bulk operations with the same API as the REST one.

Contributed by

 * Mitchel Kuijpers (Avisi)
 * Michael Nussbaum and Jack Lund (Braintree)


### Fixed unregister-query in Native Client

`clojurewerkz.elastisch.native.percolation/unregister-query` arguments
were mistakenly swapped when delegating to the Java client.

Contributed by Stephen Muss.

### Guava Excluded From Dependencies

Contributed by Jan Stępień (Stylefruits).



## Full Change Log

[Elastisch change log](https://github.com/clojurewerkz/elastisch/blob/master/ChangeLog.md) is available on GitHub.


## Thank You, Contributors

Kudos to Michael Nussbaum and Jeffrey Erikson for contributing to this release.


## Elastisch is a ClojureWerkz Project

[Elastisch](http://clojureelasticsearch.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Elastisch, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
