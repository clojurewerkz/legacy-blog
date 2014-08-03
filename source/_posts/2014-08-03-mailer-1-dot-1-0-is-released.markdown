---
layout: post
title: "Mailer 1.1.0 is Released"
date: 2014-08-03 07:00:11 +0400
comments: false
categories:
  - mailer
  - releases
---

## TL;DR

[ClojureWerkz Mailer](https://github.com/clojurewerkz/mailer) is an
ActionMailer-inspired mailer library for Clojure.

`1.1.0` is a minor feature release.


## Changes Between 1.0.0 and 1.1.0

### Support for Alternative Email Bodies

`build-email` and `deliver-email` now take extra set of template,
data, content-type for alternative email body. This is useful for
supplying alternative plain-text body in addition to main HTML
body of the message.

``` clojure
(build-email {:from "Joe The Robot", :to ["ops@megacorp.internal" "oncall@megacorp.internal"] :subject "Hello!"}
             "templates/html_hello.mustache" {:name "Joe"} :text/html
             "templates/hello.mustache" {:name "Joe"} :text/plain)
```

Contributed by Lei.


## Mailer is a ClojureWerkz Project

Mailer is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Cassaforte](http://clojurecassandra.info), a Clojure client for Cassandra built around CQL
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Neocons](http://clojureneo4j.info), a Clojure client for the Neo4J REST API

and several others. If you like Mailer, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).

## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz Team](http://twitter.com/clojurewerkz).
