---
layout: post
title: "Neocons 2.0.0-rc1 is released"
date: 2013-10-26 14:05
comments: false
categories: 
  - neocons
  - releases
---

## TL;DR

Neocons is a feature rich idiomatic [Clojure client for the Neo4J REST API](http://clojureneo4j.info).

`2.0.0-rc1` is a release candidate.  It is 100% backwards compatible with `1.1` and has one breaking
API change compared to `2.0.0-beta3`.

[Neocons documentation](http://clojureneo4j.info) has been updated to cover the new features in Neocons 2 and Neo4J.



## Changes between Neocons 2.0.0-beta3 and 2.0.0-rc1

### Renamed Function

Renamed the `clojurewerkz.neocons.rest.constraints/drop` to
`clojurewerkz.neocons.rest.constraints/drop-unique` for future
portability.


## Documentation Updates

[Neocons documentation](http://clojureneo4j.info) has been updated to cover the new features in Neocons 2 and Neo4J:

 * [Transactions](http://clojureneo4j.info/articles/populating.html#performing_operations_in_a_transaction_neo4j_20)
 * [Labels](http://clojureneo4j.info/articles/populating.html#node_labels_neo4j_20)
 * [Schema and Constraints](http://clojureneo4j.info/articles/populating.html#schema__constraints_neo4j_20)


## Change Log

We encourage all users to give this version (and Neo4J 2.0!) a try.

[Neocons change
log](https://github.com/michaelklishin/neocons/blob/master/ChangeLog.md)
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
