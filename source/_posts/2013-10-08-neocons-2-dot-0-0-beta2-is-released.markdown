---
layout: post
title: "Neocons 2.0.0-beta2 is released"
date: 2013-10-08 21:44
comments: false
categories: 
  - neocons
  - releases
---

## TL;DR

Neocons is a feature rich idiomatic [Clojure client for the Neo4J REST API](http://clojureneo4j.info).

`2.0.0-beta2` is a development milestone that targets Neo4J 2.0 and drops Clojure 1.3
support but otherwise is backwards compatible.

With this release, we begin introducing [new features](http://blog.neo4j.org/2013/08/summer-release-neo4j-20-milestone-4.html) to Neocons that are specific
to Neo4J 2.0.


## Changes between Neocons 1.1.0 and 2.0.0-beta2

### Clojure 1.3 Support Dropped

Neocons no longer supports Clojure 1.3.

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

The first argument is the variable which holds the transaction information. The second argument to the macro is `commit-on-success`, which commits the transaction there are no errors.



## Change Log

We encourage all users to give this version (and Neo4J 2.0!) a try.

[Neocons change log](https://github.com/michaelklishin/neocons/blob/master/ChangeLog.md) is available on GitHub.




## Neocons is a ClojureWerkz Project

[Neocons](http://clojureneo4j.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Neocons, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
