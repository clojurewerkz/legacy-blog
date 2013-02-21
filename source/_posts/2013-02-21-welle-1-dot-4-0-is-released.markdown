---
layout: post
title: "Welle 1.4.0 is released"
date: 2013-02-21 13:15
comments: false
categories:
  - welle
  - releases
---

## TL;DR

Welle is an expressive [Clojure client for Riak](http://clojureriak.info) with batteries included.

[1.4.0](https://clojars.org/com.novemberain/welle/versions/1.4.0) is a minor release
that is *100% backwards-compatible* with `1.3.x`. This version has been tested against
Riak `1.2.x` as well as RCs of Riak `1.3.0`.


## Changes between Welle 1.3.0 and 1.4.0

### Riak 1.3.0 Ready

Welle `1.4.0` has been tested against the upcoming Riak `1.3.0` release.

### Tombstones Handling

In eventually consistent systems such as Riak, deleted objects may
sometimes "reappear" due to concurrent modifications.  Welle by
default will filter out tombstones in
`clojurewerkz.welle.kv/fetch`. If you want to retrieve all objects
including tombstones, pass `:return-deleted-vlock` as `true` to
`clojurewerkz.welle.kv/fetch`. This behavior is new in Welle `1.4.0`
which uses Riak Java client `1.1.0`.

### Riak Java Client Update

Welle now uses [Riak Java client 1.1.0](http://lists.basho.com/pipermail/riak-users_lists.basho.com/2013-February/011094.html).

### Cheshire Update

[Cheshire](https://github.com/dakrone/cheshire/) dependency has been upgraded to version `5.0.2`.

### clojurewekz.welle.kv/delete-all Is No Longer Lazily Evaluated

Contributed by Renaud Tircher.

### Automatic Deserialization Support For clojurewerkz.welle.kv/store

`clojurewerkz.welle.kv/store`, when used with the `:return-body` option, now will automatically deserialize it
the same way `clojurewerkz.welle.kv/fetch` and `clojurewerkz.welle.kv/fetch-one` do.

Suggested by Allen Johnson.

### clj-http Update

[clj-http](https://github.com/dakrone/clj-http/) dependency has been upgraded to version `0.6.4`.

### HTTP Cluster Connection URLs

Updated HTTP cluster connections to be full URLs.  This change is
primarily to allow users to specify alternate ports.

HTTP cluster connections now require a full url:

``` clojure
(require '[clojurewerkz.welle.core :as wc])

(wc/connect-to-cluster! ["http://node1:8098/riak" "http://node2:8098/riak"])
```

Also included in this change:

`clojurewerkz.welle.core/default-port` removed and replaced by the following:

  * `clojurewerkz.welle.core/default-http-port`
  * `clojurewerkz.welle.core/default-pb-port`

### Reasonable Vclock Pruning Defaults

Welle now uses reasonable vclock pruning setting defaults in `clojurewerkz.welle.buckets/update`.

Kudos to @mefesto for reporting the issue.



## Change Log

We recommend all users to upgrade to [1.4.0](https://clojars.org/com.novemberain/welle/versions/1.4.0) a try.

[Welle change log](https://github.com/michaelklishin/welle/blob/master/ChangeLog.md) is available on GitHub.



## Welle is a ClojureWerkz Project

[Welle](http://clojureriak.info) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](http://clojureneo4j.info), a feature rich idiomatic Clojure client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Welle, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
