---
layout: post
title: "Elastisch 2.0.0-beta1 is released"
date: 2014-03-10 14:24:44 +0400
comments: false
categories:
  - elastisch
  - elasticsearch
  - releases
---

## TL;DR

Elastisch is a battle tested, small but feature rich and well
documented [Clojure client for
ElasticSearch](http://clojureelasticsearch.info).  It supports
virtually every Elastic Search feature and has [solid
documentation](http://clojureelasticsearch.info).

[2.0.0-beta1](https://clojars.org/clojurewerkz/elastisch/versions/2.0.0-beta1) is a preview
release of Elastisch 2.0, which focuses on ElasticSearch 1.0 compatibility.


## Changes between Elastisch 1.4.0 and 2.0.0

### ElasticSearch 1.0 Compatibility

Main goal of Elastisch 2.0 is ElasticSearch 2.0 compatibility. This includes minor
API changes (in line with [ElasticSearch 1.0 API and terminology changes](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/breaking-changes.html))
and moderate internal modifications.


### Support for cluster nodes stats and info REST APIs

`clojureworkz.elastisch.rest.admin/nodes-info` and `clojureworkz.elastisch.rest.admin/nodes-stats`
are new administrative functions that provide access to ElasticSearch
[cluster stats and node info](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/cluster-nodes-info.html).

Examples:

``` clojure
(require '[clojurewerkz.elastisch.rest.admin :as admin])

(admin/nodes-stats)
(admin/nodes-stats :nodes "_all")
(admin/nodes-stats :nodes ["node1" "node2"] ["indices" "os" "plugins"])

(admin/nodes-info)
(admin/nodes-info :nodes "_all")
(admin/nodes-info :nodes ["node1" "node2"] ["indices" "os" "plugins"])
```

See [ElasticSearch nodes stats
documentation](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/cluster-nodes-stats.html),
[nodes info
page](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/cluster-nodes-info.html),
and [node specification
page](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/cluster.html#cluster-nodes)
for more info.

Contributed by Joachim De Beule.

### Support for _cluster/state REST API

Added `(clojureworkz.elastisch.rest.admin/cluster-state & {:as params})`

Examples:

``` clojure
(require '[clojurewerkz.elastisch.rest.admin :as admin])

(admin/cluster-state)
(admin/cluster-state :filter_nodes true)
```

See [ElasticSearch documentation](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/cluster-state.html) for more info.

Contributed by Joachim De Beule.


### Support for _cluster/health REST API

Added `(clojureworkz.elastisch.rest.admin/cluster-health & {:as params})`

Example:

``` clojure
(require '[clojurewerkz.elastisch.rest.admin :as admin])

(admin/cluster-health)
(admin/cluster-health :index "index1")
(admin/cluster-health :index ["index1","index2"])
(admin/cluster-health :index "index1" :pretty true :level "indices")
```

See [ElasticSearch documentation](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/cluster-health.html) for more info.

Contributed by Joachim De Beule.


### Support for analyze in REST API client

Added `(doc/analyze text & {:as params})`

See [ElasticSearch documentation](http://www.elasticsearch.org/guide/en/elasticsearch/reference/current/indices-analyze.html) for more info.

Examples:

``` clojure
(require '[clojurewerkz.elastisch.rest.document :as doc])

(doc/analyze "foo bar baz")
(doc/analyze "foo bar baz" :index "some-index-name")
(doc/analyze "foo bar baz" :analyzer "whitespace")
(doc/analyze "foo bar baz" :tokenizer "keyword" :filters "lowercase")
(doc/analyze "foo bar baz" :index "some-index-name" :field "some-field-name")
```

Contributed by Joachim De Beule


### Query String Escaping

`clojurewerkz.elastisch.query/query-string` accepts a new option, `:escape-with`,
which is a function that performs escaping of special characters in query string
queries.

By default `clojurewerkz.elastisch.escape/escape-query-string-characters` is used.

Contributed by Ben Reinhart (Groupon).


### ElasticSearch Native Client Upgrade

Elastisch now depends on ElasticSearch native client version `1.0.1`.


### clj-http Update

[clj-http](https://github.com/dakrone/clj-http/) dependency has been upgraded to version `0.9.0`.



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
