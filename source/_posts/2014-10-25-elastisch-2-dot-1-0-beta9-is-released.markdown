---
layout: post
title: "Elastisch 2.1.0-beta9 is released"
date: 2014-10-25 00:45:37 +0400
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

[2.1.0-beta1](https://clojars.org/clojurewerkz/elastisch/versions/2.1.0-beta1) is a preview
release of Elastisch 2.1 which introduces a minor feature.

## Changes between Elastisch 2.1.0-beta8 and 2.1.0-beta9

### Ability to Specify Aliases In index.create-template

`clojurewerkz.elastisch.rest.index.create-template` now supports
the `:aliases` option:

``` clojure
(require '[clojurewerkz.elastisch.rest.index :as idx])

(idx/create-template conn "accounts" {:template "account*" :settings {:index {:refresh_interval "60s"}} :aliases {:account-alias {}}})
```

Contributed by Jeffrey Erikson.




## Changes between Elastisch 2.1.0-beta7 and 2.1.0-beta8

### clj-http Update

[clj-http](https://github.com/dakrone/clj-http/) dependency has been upgraded to version `1.0.x`.

### Allow Retry On Conflict Option

Updates and upserts now allow the `retry-on-conflict` option to be set.
This helps to work around Elasticsearch version conflicts.

GH issue: [#119](https://github.com/clojurewerkz/elastisch/issues/119).

Contributed by Michael Nussbaum (Braintree).


## Changes between Elastisch 2.1.0-beta6 and 2.1.0-beta7

### REST API Bulk Indexing Filters Out Operation Keys

`clojurewerkz.elastisch.rest.bulk/bulk-index` now filters out
all operation/option keys so that they don't get stored in the document
body.

GH issue: [#116](https://github.com/clojurewerkz/elastisch/issues/116).

Contributed by Michael Nussbaum (Braintree).


## Full Change Log

[Elastisch change log](https://github.com/clojurewerkz/elastisch/blob/master/ChangeLog.md) is available on GitHub.


## Thank You, Contributors

Kudos to Michael Nussbaum and Jeffrey Erikson for contributing to this release.


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


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
