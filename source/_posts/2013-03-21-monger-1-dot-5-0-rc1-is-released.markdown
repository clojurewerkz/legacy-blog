---
layout: post
title: "Monger 1.5.0-rc1 is released"
date: 2013-03-21 02:02
comments: false
categories: 
  - monger
  - releases
---

## TL;DR

Monger is an idiomatic [Clojure MongoDB driver](http://clojuremongodb.info) for a more civilized age.
It has batteries included, offers powerful expressive query DSL, strives to support every MongoDB 2.0+ feature and has sane defaults.
It also has [solid documentation](http://clojuremongodb.info).

`1.5.0` is a minor *completely backwards-compatible* release that includes updated
dependencies, MongoDB 2.4's full text search support and various minor improvements.


### Full Text Search Support

Full text search in MongoDB 2.4 can be used via commands but Monger 1.5 also provides
convenience functions in the `monger.search` namespace:

 * `monger.search/search` for performing queries
 * `monger.search/results-from` for obtaining hit documents sorted by score

``` clojure
(require '[monger.collection :as mc])
(require '[monger.search     :as ms])

(mc/ensure-index coll {:subject "text" :content "text"})
(mc/insert coll {:subject "hello there" :content "this should be searchable"})
(mc/insert coll {:subject "untitled" :content "this is just noize"})

(println (ms/results-from (ms/search coll "hello"))
```


### MongoDB Java Driver Update

MongoDB Java driver dependency has been [updated to 2.11.0](https://github.com/mongodb/mongo-java-driver/wiki/Release-Notes).


### New Geospatial Operators

`monger.operators` now defines a few more operators for convenience:

 * `$getWithin`
 * `$getIntersects`
 * `$near`

Of course, these and any other new operators can be passed as strings (e.g. `"$near"`)
as well.


### monger.core/admin-db

`monger.core/admin-db` is a new convenience function that returns the `admin` database
reference.

### monger.command/admin-command

`monger.command/admin-command` is a new convenience function for running commands
on the `admin` database.


### monger.core/mongo-options Updates

`monger.core/mongo-options` options are now up-to-date with the most recent
MongoDB Java driver.

### Factory DSL Is Gone

Monger's factory DSL (an undocumented experimental feature) has been removed from `monger.testkit`. It did
not work as well as we expected and there are better alternatives available now.


### Clojure 1.5 By Default

Monger now depends on `org.clojure/clojure` version `1.5.1`. It is still compatible with Clojure 1.3+ and if your `project.clj` depends
on a different version, it will be used, but 1.5 is the default now.

We encourage all users to upgrade to 1.5, it is a drop-in replacement for the majority of projects out there.

### Authentication On Default Database

`monger.core/authenticate` now has a 2-arity version that will authenticate
on the default database:

``` clojure
(let [username "myservice"
      pwd      "LGo5h#B`cTRQ>28tba6u"]
  (monger.core/use-db! "mydb")
  ;; authenticates requests for mydb
  (monger.core/authenticate username (.toCharArray pwd)))
```

### ClojureWerkz Support Upgrade

ClojureWerkz Support dependency has been updated to version `0.15.0`.
This means Monger now will use Cheshire `5.0.x`.


### Explicit DBCursor Closure by monger.collection/find-maps and the like

`monger.collection/find-maps` and the like will now explicitly close DB cursors.

GH issue: 47



## Change Log

[Monger change log](https://github.com/michaelklishin/monger/blob/master/ChangeLog.md) is available on GitHub.



## Monger is a ClojureWerkz Project

[Monger](http://clojuremongodb.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Monger, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[@michaelklishin](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
