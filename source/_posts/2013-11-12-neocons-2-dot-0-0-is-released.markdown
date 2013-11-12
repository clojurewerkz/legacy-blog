---
layout: post
title: "Neocons 2.0.0 is released"
date: 2013-11-12 04:28
comments: false
categories:
  - neocons
  - neo4j
  - releases
---

## TL;DR

Neocons is a feature rich idiomatic [Clojure client for the Neo4J REST API](http://clojureneo4j.info).

`2.0.0` is a major release that targets Neo4J 2.0. It is backwards
compatible with `1.1`. Note that Neo4J 2.0 contains some breaking
Cypher syntax changes.

[Neocons documentation](http://clojureneo4j.info) has been updated to cover the new features in Neocons 2 and Neo4J.



## Changes between Neocons 1.1.0 and 2.0.0

### Transaction Support (Neo4J Server 2.0)

Neocons 2.0 gains support for [transactions](http://docs.neo4j.org/chunked/milestone/rest-api-transactional.html).


#### Higher Level API

A group of Cypher statements can be executed in a transaction
that will be committed automatically upon success. Any error
during the execution will trigger a rollback.

``` clojure
(require '[clojurewerkz.neocons.rest.transaction :as tx])

(tx/in-transaction
  (tx/statement "CREATE (n {props}) RETURN n" {:props {:name "Node 1"}})
  (tx/statement "CREATE (n {props}) RETURN n" {:props {:name "Node 2"}}))
```

#### Lower Level API

Transactions are instantiated from a group of Cypher statements
that are passed as maps to `clojurewerkz.neocons.rest.transaction/begin`:

``` clojure
(let [t (tx/begin-tx [{:statement "CREATE (n {props}) RETURN n" {:props {:name "My node"}}}])]
  (tx/commit t))

(let [t (tx/begin-tx)]
  (tx/rollback t))
```

`clojurewerkz.neocons.rest.transaction/commit` and
`clojurewerkz.neocons.rest.transaction/rollback` commit
and roll a transaction back, respectively.

#### Macro for working with a transaction

If you want a more fine grained control of working in a transaction without manually
committing or checking for exceptions, you can use the
`clojurewerkz.neocons.rest.transaction/with-transaction` macro.

``` clojure
(require '[clojurewerkz.neocons.rest.transaction :as tx])

(let [transaction (tx/begin-tx)]
  (tx/with-transaction
    transaction
    true
    (let [[_ result] (tx/execute transaction [(tx/statement "CREATE (n) RETURN ID(n)")])]
    (println result))))
```

If there any errors while processing, the transaction is rolled back.

The first argument is the variable which holds the transaction
information. The second argument to the macro is `commit-on-success`,
which commits the transaction there are no errors.



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


### Clojure 1.6 Compatibility Fixes

Neocons 2.0 is compatible with recent
releases of Clojure 1.6 (master).



### Clojure 1.3 Support Dropped

Neocons no longer supports Clojure 1.3.



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


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the
[ClojureWerkz](http://clojurewerkz.org) Team
