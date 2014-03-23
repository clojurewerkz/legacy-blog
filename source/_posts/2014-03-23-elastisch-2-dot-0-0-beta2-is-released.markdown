---
layout: post
title: "Elastisch 2.0.0-beta2 is released"
date: 2014-03-23 22:36:58 +0400
comments: false
categories:
  - elastisch
  - elasticsearch
  - releases
---

## TL;DR

Elastisch is a battle tested, small but feature rich and well
documented [Clojure client for
ElasticSearch](http://clojureelasticsearch.info). It supports
virtually every Elastic Search feature and has [solid
documentation](http://clojureelasticsearch.info).

[2.0.0-beta2](https://clojars.org/clojurewerkz/elastisch/versions/2.0.0-beta2)
is a preview release of Elastisch 2.0, which focuses on the new
features in ElasticSearch 1.0.


## Changes between Elastisch 2.0.0-beta1 and 2.0.0-beta2

### (Improved) Aggregation Support

Elastisch 2.0 features multiple convenience functions for working with
[ElasticSearch aggregations](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/search-aggregations.html).

`clojurewerkz.elastisch.aggregation` is a new namespace that contains
helper functions that produce various types of aggregations. Just like
`clojurewerkz.elastisch.query`, all of the functions return maps and
are optional.

`clojurewerkz.elastisch.rest.response/aggregations-from` is a new function
that returns aggregations from a search response:

``` clojure
(require '[clojurewerkz.elastisch.rest.document :as doc])
(require '[clojurewerkz.elastisch.query :as q])
(require '[clojurewerkz.elastisch.aggregation :as a])
(require '[clojurewerkz.elastisch.rest.response :refer [aggregations-from]])

(let [index-name   "people"
        mapping-type "person"
        response     (doc/search index-name mapping-type
                                 :query (q/match-all)
                                 :aggregations {:min_age (a/min "age")})
        agg          (aggregation-from response :min_age)]
    (is (= {:value 22.0} agg)))
```

Aggregations support is primarily focused on REST client at the moment.

### clj-http Update

[clj-http](https://github.com/dakrone/clj-http/) dependency has been upgraded to version `0.9.1`.



## Full Change Log

[Elastisch change log](https://github.com/clojurewerkz/elastisch/blob/master/ChangeLog.md) is available on GitHub.


## Thank You, Contributors

Kudos to Richie Vos for contributing to this release.


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
