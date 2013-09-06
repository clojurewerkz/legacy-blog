---
layout: post
title: "Route One 1.0.0-rc2 is released"
date: 2013-09-06 22:26
comments: false
categories:
  - route-one
  - releases
---

[Route One](https://github.com/clojurewerkz/route-one) is a Clojure DSL for URL/URI/path generation
from a route map, compatible with Compojure's [Clout](https://github.com/weavejester/clout).

`1.0.0-rc2` is a development milestone release that further improves Compojure
integration.



## Changes between Elastisch 1.0.0-rc1 and 1.0.0-rc2

### Tight Compojure integration

It is now possible to define named Compojure routes with Route One:

```clj
(ns my-app
  (:require [compojure.core :as compojure :as compojure])
  (:use clojurewerkz.route-one.compojure))

(compojure/defroutes main-routes
  (GET about request (handlers.root/root-page request)) ;; will use /about as a template
  (GET documents request (handlers.root/documents-page request)) ;; will use /documents as a template)
```

This will generate `main-routes` in same exact manner Compojure
generates them, but will also add helper functions for building urls
(`about-path`, `about-url`, `documents-path`, `document-url` and so
on).

To use this feature, you'll have to bring in Compojure as a dependency
to your project:

```clj
[compojure "1.1.5"]
```



## Change log

[Route One change log](https://github.com/clojurewerkz/route-one/blob/master/ChangeLog.md) is available on GitHub.


## Route One is a ClojureWerkz Project

Route One is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a small feature complete Clojure client for ElasticSearch
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Titanium](http://titanium.clojurewerkz.org), a Clojure graph library
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Elastisch, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
