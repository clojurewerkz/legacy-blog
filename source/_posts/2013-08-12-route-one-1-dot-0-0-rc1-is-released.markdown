---
layout: post
title: "Route One 1.0.0-rc1 is released"
date: 2013-08-12 22:07
comments: false
categories:
  - releases
  - route-one
---

## What is Route One

[Route One](https://github.com/clojurewerkz/route-one) is a Clojure DSL for URL/URI/path generation
from a route map, compatible with Compojure's [Clout](https://github.com/weavejester/clout).

Route One is intentionally a very small library that lets you do two things:

 * Ability to define routes
 * Path generation from routes

Route One can be used as part of Web applications, mail delivery services and any other
application that needs to generate URLs using a predefined map of routes.

## Supported Clojure Versions

Route One targets Clojure 1.4+, tested against 3 Clojure versions x 3 JDKs on travis-ci.org, and is released under the Eclipse Public License.

## Documentation and Examples

Here's what Route One API looks like:

``` clojure
(ns my.app
  (:require [clojurewerkz.route-one.core :refer :all])

;; define your routes
(defroute about "/about")
(defroute faq "/faq")
(defroute help "/help")
(defroute documents "/docs/:title")
(defroute category-documents "/docs/:category/:title")
(defroute documents-with-ext "/docs/:title.:ext")

;; generate relative paths (by generated fns)
(documents-path :title "a-title") ;; => "/docs/a-title"
(documents-path :title "ohai") ;; => "/docs/ohai"

(path-for "/docs/:category/:title" { :category "greetings" :title "ohai" }) ;; => "/docs/greetings/ohai"
(path-for "/docs/:category/:title" { :category "greetings" }) ;; => IllegalArgumentException, because :title value is missing

(with-base-url "https://myservice.com"
  (url-for "/docs/title"  { :title "ohai" }) ;; => "https://myservice.com/docs/title"
  (url-for "/docs/:title" { :title "ohai" }) ;; => "https://myservice.com/docs/ohai"
  (url-for "/docs/:category/:title" { :category "greetings" :title "ohai" }) ;; => "https://myservice.com/docs/greetings/ohai"
  (url-for "/docs/:category/:title" { :category "greetings" }) ;; => IllegalArgumentException, because :title value is missing
)

;; generate relative paths (by generated fns)
(with-base-url "https://myservice.com"
  (documents-url :title "a-title") ;; => "https://myservice.com/docs/a-title"
  (documents-url :title "a-title" :category "greetings") ;; => "https://myservice.com/docs/greetings/a-title"
)
```

Learn more in the [documentation](https://github.com/clojurewerkz/route-one#documentation--examples).


## License

The source is available [on GitHub](http://github.com/clojurewerkz/route-one). We also use GitHub to track issues.


The [ClojureWerkz](http://clojurewerkz.org) Team
