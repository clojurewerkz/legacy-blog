---
layout: post
title: "Introducing Propertied"
date: 2013-10-07 21:11
comments: false
categories:
  - propertied
  - releases
---

## What is Propertied

[Propertied](https://github.com/michaelklishin/propertied) is a tiny
Clojure library that makes working with Java property lists from Clojure
a bit nicer.

It is very small in scope: convert `java.util.Properties` to and from an immutable
map, load and store them to and from `.properties` files.


## Supported Clojure Versions

Propertied targets Clojure 1.4+, tested against 3 Clojure versions x 2
JDKs on travis-ci.org, and is released under the Eclipse Public
License.

## Documentation and Examples

Propertied makes it easy to convert property lists (`java.util.Properties`) into Clojure
maps and vice versa. Thus working with property lists is generally as straightforward as
working with maps.

`clojurewerkz.propertied.properties/load-from` is a polymorphic function that
instantiates a property list from an input (e.g. a map).

`clojurewerkz.propertied.properties/properties->map`

``` clojure
(require '[clojurewerkz.propertied.properties :as p])

(p/load-from {"a key" "a value"})
;= {"a key" "a value"}
(class (p/load-from {"a key" "a value"}))
;= java.util.Properties
(let [pl (p/load-from {"a key" "a value"})]
  (p/properties->map pl))
;= {"a key" "a value"}

;; loading from files and InputStreams
(require '[clojure.java.io :as io])

(p/load-from (io/resource "resource/on/classpath.properties"))
(p/load-from (io/file "resource/on/classpath.properties"))

;; storing to property files (.properties)
(p/store-to {"name" "Michael" "age" "28"} "/tmp/michael.properties")
(p/store-to {"name" "Michael" "age" "28"} (io/file "/tmp/michael.properties"))
(p/store-to {"name" "Michael" "age" "28"} (java.io.File/createTempFile "michael" ".properties"))
```

Learn more in the [documentation](https://github.com/michaelklishin/propertied#documentation--examples).


## Community

To subscribe for announcements of releases, important changes and so on, please follow [@ClojureWerkz](https://twitter.com/#!/clojurewerkz) on Twitter.



## License

The source is available [on
GitHub](http://github.com/michaelklishin/propertied). We also use
GitHub to track issues.


The [ClojureWerkz](http://clojurewerkz.org) Team
