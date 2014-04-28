---
layout: post
title: "Balagan 1.0.0 is released"
date: 2014-04-28 23:51:29 +0400
comments: false
categories:
  - balagan
  - releases
---

## What is Balagan

[Balagan](https://github.com/clojurewerkz/balagan) is a tiny
Clojure library for data structure transformation inspired by
[Enlive](https://github.com/cgrand/enlive).


## Supported Clojure Versions

Balagan targets Clojure 1.4+, tested against 3 Clojure versions x 2
JDKs on travis-ci.org, and is released under the Eclipse Public
License.

## Documentation and Examples

Balagan builds on ideas from [Enlive](https://github.com/cgrand/enlive). It may help to get familiar with them
first.

Let's say you're working on a Data Access layer for the application. You have a user entry
represented as hash:

```clojure
(def user
  {:name "Alex"
   :birth-year 1990
   :nickname "ifesdjeen"})
```

### Transformation

Now, we can start transforming users the way we want: add, remove fields based on certain conditions.

```clojure
(update user
           []                  (add-field :cool-dude true) ;; adds a field :cool-dude with value true
           (new-path [:age])   #(- 2014 (:birth-year %))   ;; explicit adding of a new field, calculated from the existing data
           (new-path [:posts]) #(fetch-posts (:name %))    ;; fetching some related data from the DB
           [:posts :*]         #(update-posts %))       ;; apply some transformations to all the fetched posts, if there are any
```

### Queries

Queries are very similar to how you'd query your data with `filter` in Clojure:

```clj
(let [data {:a {:b [{:c 1} {:c 2} {:c 3}]
                :d [{:c 5} {:c 6} {:c 7}]}}]
  (select data  [:* :* even? :c]))
;; => (1 3 5 7)  
```

Results are returned in the order they've been seen in your data structure, however you should be aware of the 
fact that iterating over the hash in Clojure doesn't guarantee you order.

### Path Queries

Path queries are most useful when you'd like to fire a function against some part of your data (be it processing,
database initialization or anything else.

You can also run predicate queries based on your map, for example if you want to configure your database servers
from rather big and complex config:

```clj
(def conf {:db
           {:redis {:cache  [{:host "host01" :port 1234} {:host "host02" :port 1234}]
                    :pubsub [{:host "host01" :port 1234} {:host "host02" :port 1234}]}}
           :cassandra [{:host "host01"} {:host "host02"}]})

(with-paths conf
        [:db :redis :cache]  configure-redis-cache
        [:db :redis :pubsub] configure-redis-pubsub
        [:db :cassandra]     configure-cassandra)
```

In this example, `configure-redis-cache` funciton will receive two arguments: `value` and `path`:

```clj
(defn configure-redis-cache
  [value path]
  (println "Value: " value)
  (println "Path: " path))

;; => Value: [{:host host01, :port 1234} {:host host02, :port 1234}]
;; => Path: [:db :redis :cache]
```

You can also do wildcard-matching with `:*`, for example: 

```clj
(b/select {:a {:b {:c 1} :d {:c 2}}}
          [:a :* :c] (fn [val path]
                       (if (= path [:a :b :c])
                         (is (= val 1))
                         (is (= val 2)))))

```

Learn more in the [documentation section](https://github.com/clojurewerkz/balagan#documentation-and-examples).


## Community

To subscribe for announcements of releases, important changes and so on, please follow
[@ClojureWerkz](https://twitter.com/#!/clojurewerkz) on Twitter.


## License

Distributed under the Eclipse Public License, the same as Clojure.

The source is available [on
GitHub](http://github.com/clojurewerkz/balagan). We also use
GitHub to track issues.


## About the Author

The [ClojureWerkz](http://clojurewerkz.org) Team.
