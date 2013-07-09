---
layout: post
title: "Cassaforte 1.0.1 is released"
date: 2013-07-09 19:49
comments: false
categories:
  - cassaforte
  - releases
---

## TL;DR

[Cassaforte](http://clojurecassandra.info) is a new Clojure client for
Apache Cassandra 1.2+.  It is built around CQL 3 and focuses on ease
of use. You will likely find that using Cassandra from Clojure has
never been so easy.

Cassaforte is finally a `1.0` project. This means we are confident that you will
have a good experience using it and the docs are good enough.


## Another Brick in the Wall

[ClojureWerkz projects](http://clojurewerkz.org) are mostly known for our data store clients. Data processing is a
sweet spot for Clojure and that's what we primarily use it for.

Over time we've developed and released a number of data store clients:

 * [Monger](http://clojuremongodb.info)
 * [Neocons](http://clojureneo4j.info)
 * [Welle](http://clojureriak.info)
 * [Elastisch](http://clojureelasticsearch.info)
 * [Titanium](http://titanium.clojurewerkz.org)

and a few others.

Today we are adding another client to this family, [Cassaforte](http://clojurecassandra.info).


## The Cassaforte Story

Cassaforte was started about a year ago as an experiment. Back then we needed a
database well suited for time series data, and Cassandra is a good choice. However,
dealing with existing clients, namely Hector and Astyanax, was quite a bit of a pain.

In the end, using Cassandra's low level Thrift client worked well and we have
been improving the codebase bit by bit, while working on an event collection and
analytics system.

A few months ago, DataStax released a [new Java driver for Cassandra](https://github.com/datastax/java-driver) that was
*a lot* better suited to what Cassaforte needed to power it than any other alternative.

We were able to switch Cassaforte to it in a couple of weeks. About the same time,
a great fellow [Max Penet](https://twitter.com/mpenet) released a Clojure DSL for generating CQL, [Hayt](https://github.com/mpenet/hayt).

Hayt makes working with CQL as nice as the new `clojure.java.jdbc` DSL:

``` clojure
(require '[clojurewerkz.cassaforte.cql :as cql])

(cql/prepared
   (cql/insert "users" {:name "Alex" :city "Munich")}))
(cql/prepared
   (cql/insert "users" {:name "Robert" :city "Berlin")}))

(cql/select "users" (where :name "Alex"))
;; => [{:name "Alex", :city "Munich"}]

(cql/select "users"
            (where :name [:in ["Alex" "Robert"]]))
;; => [{:name "Alex", :city "Munich"}
       {:name "Robert", :city "Berlin"}]
```

```clojure
(require '[clojurewerkz.cassaforte.cql :as cql])

;; For clarity, we select :post_id column only
(cql/select "user_posts"
            (columns :post_id)
            (where :username "Alex")
            (order-by [:post_id :desc]))
;; => [{:post_id "post3"}
       {:post_id "post2"}
       {:post_id "post1"}]
```

```clojure
(require '[clojurewerkz.cassaforte.cql :as cql])

(cql/select "user_posts"
            (columns :post_id)
            (where :username "Alex"
                   :post_id [> "post1"]
                   :post_id [< "post3"]))
;; => [{:post_id "post2"}]
```

Integrating Hayt took a few weeks as well. From there, it took some time to
write initial [documentation](http://clojurecassandra.info) and add some polish.

Major props to the DataStax team for releasing such a nice and focused Java driver
and Max for making querying Cassandra from Clojure such a good experience.


## What's In The Box

Cassaforte is young but already offers all the key features you'd expect from
such a client:

 * Schema (keyspaces, tables/column families, indices) manipulation
 * _All_ CQL operations
 * Inserts that work with Clojure data structures
 * CQL 3.0 queries, including queries with placeholders (?, a la JDBC)
 * Prepared statements
 * Counters
 * Multi-node (cluster) connections
 * Automatic deserialization of column names and values according to the schema
 * Lazy sequence-based queries over large result sets

 Needless to say, as more features are added to Cassandra and the DataStax core Java driver,
 Cassaforte will soon to follow their lead.


## Finally 1.0

It took 6 RC releases to get to Cassaforte `1.0` but it's finally here. We even already have one one patch release
out, which fixes an AOT compilation issue discovered by a user after `1.0.0` was tagged.

Cassaforte artifacts are [released to Clojars](https://clojars.org/clojurewerkz/cassaforte). If you are using Maven, add the following repository
definition to your `pom.xml`:

``` xml
<repository>
  <id>clojars.org</id>
  <url>http://clojars.org/repo</url>
</repository>
```

then add the actual dependency. With Leiningen:

``` clojure
[clojurewerkz/cassaforte "1.0.1"]
```

With Maven:

``` xml
<dependency>
  <groupId>clojurewerkz</groupId>
  <artifactId>cassaforte</artifactId>
  <version>1.0.1</version>
</dependency>
```



## Documentation

To get started, take a look at the [Getting Started guide](http://clojurecassandra.info/articles/getting_started.html).

The rest of the [guides](http://clojurecassandra.info) are being worked on.

[API reference](http://reference.clojurecassandra.info) is also available.


## Thank You, Contributors

Cassaforte was started by [Michael](http://twitter.com/michaelklishin) but ended up being a brain child of [Alex](http://twitter.com/ifesdjeen).

We would like to thank Max Penet for providing a lot useful feedback, sharing Hayt with
us and helping us define what we want Cassaforte to be and feel like.


## News and Updates

New releases and updates are announced [on
Twitter](http://twitter.com/clojurewerkz). Cassaforte also has [a
mailing list](https://groups.google.com/group/clojure-cassandra), feel
free to ask questions and report issues there.


## Cassaforte is a ClojureWerkz Project

Cassaforte is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Neocons](http://clojureneo4j.info), a Clojure client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Cassaforte, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz Team](http://twitter.com/clojurewerkz).
