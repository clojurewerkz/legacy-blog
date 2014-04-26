---
layout: post
title: "Major Breaking Public API Changes Coming in Our Projects"
date: 2014-04-26 18:13:54 +0400
comments: false
categories:
  - releases
  - philosophy
  - monger
  - elastisch
  - neocons
  - cassaforte
---

## TL;DR

If you use a [ClojureWerkz project](http://clojurewerkz.org) (or two), please
beware that libraries that rely on dynamic vars (e.g. Monger or Elastisch) will
undergo a major API revision soon. We generally try to keep things as
backwards compatible as possible but this is the right thing to do.


## Everything Should Be Made As Easy As Possible

The ClojureWerkz philosophy has always been: easy matters. With all the focus
on simplicity in the Clojure community, ease of use is often seen as a secondary
concern or outright ignored.

To paraphrase Albert Einstein, "everything should be made as easy as
possible".  This is why some of our projects (Monger, Elastisch,
Neocons, Cassaforte) historically relied on a shared dynamic var for
some commonly global state (e.g. database connection).

This makes it very easy to get started with the project and (we believe)
helped some people adopt Clojure faster and with less frustration.

## ...But Not Easier

Unfortunately, the kind of problems you face early on in software engineering
are not exactly the same as problems that arise as your project grows.

A lot of the problems have to do with scale but no the "bajillion
request per second" kind. Rather, it's about scaling your development
team, product features, and making things operationally sane.

This is where some of the library aspects that are incredibly valuable
to complete beginners are not very valuable or outright [annoying](http://stuartsierra.com/2013/03/29/perils-of-dynamic-scope) to
more experienced teams.

Overreliance on dynamic vars is by far the most common complaint we
hear about Elastisch, Monger and so on. Over time we introduced
alternative APIs ("monger.multi") or overloaded function arities to
make it easier for developers to use multiple connections when needed.
But the complaints did not end. We need to act more boldly and we will.


## Breaking Public APIs

So here's the news: next versions of Monger, Elastisch, Neocons, and Cassaforte
will make db/connection/client a **mandatory explicit argument** across the
entire public API.

In other words, instead of

``` clojure
(a-fn arg1 arg2)
```

you will have to use

``` clojure
(a-fn conn arg1 arg2)
```

To demonstrate this with a snippet of code that uses [Elastisch](http://clojureelasticsearch.info), before the change:

``` clojure
(ns clojurewerkz.elastisch.docs.examples
  (:require [clojurewerkz.elastisch.rest  :as esr]
            [clojurewerkz.elastisch.rest.index :as esi]
            [clojurewerkz.elastisch.rest.document :as esd]))

(defn -main
  [& args]
  (esr/connect! "http://127.0.0.1:9200")
  (let [mapping-types {"person" {:properties {:username   {:type "string" :store "yes"}
                                              :first-name {:type "string" :store "yes"}
                                              :last-name  {:type "string"}
                                              :age        {:type "integer"}
                                              :title      {:type "string" :analyzer "snowball"}
                                              :planet     {:type "string"}
                                              :biography  {:type "string" :analyzer "snowball" :term_vector "with_positions_offsets"}}}}
        doc           {:username "happyjoe" :first-name "Joe" :last-name "Smith" :age 30 :title "Teh Boss" :planet "Earth" :biography "N/A"}]
    (esi/create "myapp2_development" :mappings mapping-types)
    (esd/create "myapp2_development" "person" doc)))
```

After the change:

``` clojure
(ns clojurewerkz.elastisch.docs.examples
  (:require [clojurewerkz.elastisch.rest  :as esr]
            [clojurewerkz.elastisch.rest.index :as esi]
            [clojurewerkz.elastisch.rest.document :as esd]))

(defn -main
  [& args]
  (let [conn          (esr/connect "http://127.0.0.1:9200")
        mapping-types {"person" {:properties {:username   {:type "string" :store "yes"}
                                              :first-name {:type "string" :store "yes"}
                                              :last-name  {:type "string"}
                                              :age        {:type "integer"}
                                              :title      {:type "string" :analyzer "snowball"}
                                              :planet     {:type "string"}
                                              :biography  {:type "string" :analyzer "snowball" :term_vector "with_positions_offsets"}}}}
        doc           {:username "happyjoe" :first-name "Joe" :last-name "Smith" :age 30 :title "Teh Boss" :planet "Earth" :biography "N/A"}]
    (esi/create conn "myapp2_development" :mappings mapping-types)
    (esd/create conn "myapp2_development" "person" doc)))
```

The change is quite small but both radical enough to make upgrading
harder for some people *and* radically simplify app architecture for
others (no more shared state you have to work around all the time).

Two libraries are already updated: [Elastisch
2.0](https://github.com/clojurewerkz/elastisch/issues/80) and [Neocons
3.0](https://github.com/michaelklishin/neocons/pull/51).


## Thank You, Contributors

We'd like to thank [Rohit Aggarwal](https://github.com/ducky427) for
making all the changes described above for Neocons 3.0. Contributors
like Rohit is why open source software works as well as it does.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team

