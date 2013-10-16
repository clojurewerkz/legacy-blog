---
layout: post
title: "Neocons 2.0.0-beta3 is released"
date: 2013-10-16 22:11
comments: false
categories:
  - neocons
  - releases
---

## TL;DR

Neocons is a feature rich idiomatic [Clojure client for the Neo4J REST API](http://clojureneo4j.info).

`2.0.0-beta3` is a development milestone that adds support to
remaining Neo4J 2.0 features.  It is 100% backwards compatible.



## Changes between Neocons 2.0.0-beta2 and 2.0.0-beta3

### Constraints Support (Neo4J 2.0 Only)

`clojurewerkz.neocons.rest.constraints` is a new namespace that
implements [Neo4J 2.0 constraints](http://docs.neo4j.org/chunked/milestone/rest-api-schema-constraints.html).

``` clojure
(require '[clojurewerkz.neocons.rest.constraints :as cts])

;; create a uniqueness constraint
(cts/create-unique "Person" :name)

;; get constraint info
(cts/get-unique "Person" :name)

;; drop a constraint
(cts/drop "Person" :name)
```



### Labels Support (Neo4J 2.0 Only)

`clojurewerkz.neocons.rest.labels` is a new namespace that provides
support for [labels in Neo4J 2.0](http://docs.neo4j.org/chunked/milestone/rest-api-node-labels.html).

It is possible to add, replace, remove and retrieve labels to/from a node.

To add labels to a node, use `clojurewerkz.neocons.rest.labels/add`:

``` clojure
(require '[clojurewerkz.neocons.rest.labels :as nl])

(nl/add node ["neo4j" "clojure"])
```

To add replaces all labels on a node, use `clojurewerkz.neocons.rest.labels/replace`:

``` clojure
(require '[clojurewerkz.neocons.rest.labels :as nl])

(nl/replace node ["graph" "database"])
```

Deleting a label from a node is possible with `clojurewerkz.neocons.rest.labels/remove`:

``` clojure
(require '[clojurewerkz.neocons.rest.labels :as nl])

(nl/remove node "database")
```

`clojurewerkz.neocons.rest.labels/get-all-labels` is the function that lists
either all labels in the database (w/o arguments) or on a specific node
(1-arity):

``` clojure
(require '[clojurewerkz.neocons.rest.labels :as nl])

(nl/get-all-labels node)
;= [all labels]
(nl/get-all-labels node)
;= [labels on node]
```


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
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Neocons, you may also like [our other
projects](http://clojurewerkz.org).

Let us know what you think [on
Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing
list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the
[ClojureWerkz](http://clojurewerkz.org) Team
