---
layout: post
title: "Cassaforte 2.0.0-rc1 is released"
date: 2014-11-26 00:47:33 +0300
comments: false
categories:
  - cassaforte
  - releases
---

## TL;DR

[Cassaforte](http://clojurecassandra.info) is a Clojure client for
Apache Cassandra. It is built around CQL 3 and focuses on ease
of use. You will likely find that using Cassandra from Clojure has
never been so easy.

`2.0.0-rc` is a release candidate for 2.0.


## Changes between 1.3.x and 2.0.0-rc1

Compared to 1.3.x, `2.0.0-rc1` has one major [breaking API change](http://blog.clojurewerkz.org/blog/2014/04/26/major-breaking-public-api-changes-coming-in-our-projects/).

### Client (Session) is Explicit Argument

All Cassaforte public API functions that issue requests to Cassandra now require
a client (session) to be passed as an explicit argument:

```clj
(ns cassaforte.docs
  (:require [clojurewerkz.cassaforte.client :as cc]
            [clojurewerkz.cassaforte.cql    :as cql]))

(let [conn (cc/connect ["127.0.0.1"])]
  (cql/use-keyspace conn "cassaforte_keyspace"))
```

```clj
(ns cassaforte.docs
  (:require [clojurewerkz.cassaforte.client :as cc]
            [clojurewerkz.cassaforte.cql    :as cql]
            [clojurewerkz.cassaforte.query :refer :all]))

(let [conn (cc/connect ["127.0.0.1"])]
  (cql/create-table conn "user_posts"
                (column-definitions {:username :varchar
                                     :post_id  :varchar
                                     :body     :text
                                     :primary-key [:username :post_id]})))
```

```clj
(ns cassaforte.docs
  (:require [clojurewerkz.cassaforte.client :as cc]
            [clojurewerkz.cassaforte.cql    :as cql]))

(let [conn (cc/connect ["127.0.0.1"])]
  (cql/insert conn "users" {:name "Alex" :age (int 19)}))
```

### Hayt Upgraded to 2.0

[Hayt](https://github.com/mpenet/hayt) was upgraded to 2.0.

### clojurewerkz.cassandra.cql/iterate-table Now Terminates

`clojurewerkz.cassandra.cql/iterate-table` no longer produces an infinite
sequence.


### URI Connections

It is now possible to connect to a node and switch to a namespace
using a URI string:

``` clojure
(ns cassaforte.docs
  (:require [clojurewerkz.cassaforte.client :as cc]))

;; connects to node 127.0.0.1:9042 and uses "new_cql_keyspace" as keyspace
(cc/connect-with-uri "cql://127.0.0.1:9042/new_cql_keyspace")
```

### Cassandra 2.1 Compatibility

Cassaforte 2.0 is compatible with Cassandra 2.1.


### Prepared Statement Cache Removed

Prepared statement cache was affecting client correctness in some cases
and was removed.


### Policy Namespace

Policy-related functions from `clojurewerkz.cassaforte.client` were extracted into
`clojurewerkz.cassaforte.policies`:

```clojure
(require '[clojurewerkz.cassaforte.policies :as cp])

(cp/exponential-reconnection-policy 100 1000)
```

``` clojure
(require '[clojurewerkz.cassaforte.policies :as cp])

(let [p (cp/round-robin-policy)]
  (cp/token-aware-policy p))
```

### DataStax Java Driver Update

DataStax Java driver has been updated to `2.1.x`.


### Cassandra Sessions Compatible with with-open

`Session#shutdown` was renamed to `Session#close` in
cassandra-driver-core. Cassaforte needs to be adapted to that.

Contributed by Jarkko Mönkkönen.

### TLS and Kerberos Support

Cassaforte now supports TLS connections and Kerberos authentication
via [DataStax CQL extensions](http://www.datastax.com/dev/blog/accessing-secure-dse-clusters-with-cql-native-protocol).

The `:ssl` connection option now can be a map with two keys:

 * `:keystore-path`
 * `:keystore-password`

which provide a path and password to a [JDK KeyStore](http://docs.oracle.com/javase/7/docs/api/java/security/KeyStore.html)
on disk, created with
[keytool](http://docs.oracle.com/javase/7/docs/technotes/tools/solaris/keytool.html).

Optionally, an instance of
[SSLOptions](http://www.datastax.com/drivers/java/2.0/com/datastax/driver/core/SSLOptions.html)
can be provided via the `:ssl-options` connection option.

Contributed by Max Barnash.


### Clojure 1.4 and 1.5 Support Dropped

Cassaforte now requires Clojure `1.6.0`.

### Collections Converted to Clojure Data Structures

Cassandra maps, sets and lists are now automatically converted to their
immutable Clojure counterparts.

### Atomic Batches Support

[Atomic batches](http://www.datastax.com/documentation/cql/3.1/cql/cql_reference/batch_r.html) are now easier to use with Cassaforte:

``` clojure
(require '[clojurewerkz.cassaforte.client :as client])
(require '[clojurewerkz.cassaforte.cql :as cql :refer :all])
(require '[clojurewerkz.cassaforte.query :refer :all])
(require '[qbits.hayt.dsl.statement :as hs])

(let [s (client/connect ["127.0.0.1"])]
  (cql/atomic-batch s (queries
                         (hs/insert :users (values {:name "Alex" :city "Munich" :age (int 19)}))
                         (hs/insert :users (values {:name "Fritz" :city "Hamburg" :age (int 28)})))))
```

### Query DSL Taken From Hayt 2.0

Cassaforte no longer tries to support query condition DSLs for both Hayt 1.x
and Hayt 2.0. Hayt 2.0 is the only supported flavour now and
is the future.

Some examples of the changes:

``` clojure
;; before
(where :name "Alex")

;; after
(where [[= :name "Alex"]])
(where {:name "Alex"})


;; before
(where :name "Alex" :city "Munich")

;; after
(where [[= :name "Alex"]
        [= :city "Munich"]])
(where {:name "Alex" :city "Munich"})


;; before
(where :name "Alex" :age [> 25])

;; after
(where [[= :name "Alex"]
        [> :age  25]])

;; before
(where :name "Alex" :city [:in ["Munich" "Frankfurt"]])

;; after
(where [[= :name "Alex"]
        [:in :city ["Munich" "Frankfurt"]]])
```

As it's easy to see, the new condition style closer resembles
Clojure itself and thus was a reasonable decision on behalf of Hayt
developers.


### Keyspace as Option

It is now possible to choose keyspace via an option:

``` clojure
(ns cassaforte.docs
  (:require [clojurewerkz.cassaforte.client :as cc]))

(let [conn (cc/connect {:hosts ["127.0.0.1"] :keyspace "a-keyspace"})]
  )
```

Contributed by Max Barnash (DataStax).


### Clojure 1.7.0-alpha2+ Compatibility

Cassaforte is now compatible with Clojure `1.7.0-alpha2` and later versions.


GH issue: [#60](https://github.com/clojurewerkz/cassaforte/pull/60).

### Support for overriding default SSL cipher suites

Providing a `:cipher-suites` key in the `:ssl` connection option allows to specify cipher suites
that are enabled when connecting to a cluster with SSL.
The value of this key is a Seq of Strings (e.g. a vector) where each item specifies a cipher suite:

```clj
(ns cassaforte.docs
  (:require [clojurewerkz.cassaforte.client :as cc]))

(cc/build-cluster {:ssl {:keystore-path "path/to/keystore"
                         :keystore-password "password"}})]
                         :cipher-suites ["TLS_RSA_WITH_AES_128_CBC_SHA"]}}
```

The `:cipher-suites` key is optional and may be omitted, in which case Datastax Java driver's
default cipher suites (`com.datastax.driver.core.SSLOptions/DEFAULT_SSL_CIPHER_SUITES`) are enabled.

This can be used to work around the need to install Java Cryptography Extension (JCE) Unlimited Strength
Jurisdiction Policy Files required by the default set of cipher suites. `TLS_RSA_WITH_AES_128_CBC_SHA`
is a suite in the default set that works with the standard JCE. E.g. by specifying just that one,
as in the code example, the standard JCE is enough.

Contributed by Juhani Hietikko.

GH issue: [#61](https://github.com/clojurewerkz/cassaforte/pull/61).



## News and Updates

New releases and updates are announced [on Twitter](http://twitter.com/clojurewerkz). Cassaforte also has [a
mailing list](https://groups.google.com/group/clojure-cassandra), feel
free to ask questions and report issues there.


## Cassaforte is a ClojureWerkz Project

Cassaforte is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [EEP](http://github.com/clojurewerkz/eep), a Clojure library for stream (event) processing
 * [Neocons](http://clojureneo4j.info), a Clojure client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Cassaforte, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz Team](http://twitter.com/clojurewerkz).
