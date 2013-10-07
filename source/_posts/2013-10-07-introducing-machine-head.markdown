---
layout: post
title: "Introducing Machine Head"
date: 2013-10-07 21:45
comments: false
categories:
  - machine_head
  - releases
---

## Why Messaging Matters for Emerging Languages

Over the last 6-7 years we have been observing how companies adopt
emerging technologies.  Younger languages such as Clojure may enjoy
completely green field projects every now and then, but most of the
time, they have to integrate into existing systems.

Back when ClojureWerkz "founders" started adopting Clojure, the very first project
we had to develop was [Langohr](http://clojurerabbitmq.info). Langohr is
a RabbitMQ client that made it possible for us to build services in Clojure
that interoperate with other applications (in Ruby and C). That worked
very well and messaging keeps being one of our primary integration strategies.

Today we are happy to announce another project in the same space:
[Machine Head](http://clojuremqtt.info).


## What is Machine Head

[Machine Head](https://github.com/clojurewerkz/machine_head) is a minimalistic
Clojure MQTT (v3.1) client built on top of Eclipse Paho.

MQTT is an efficient messaging protocol that was designed for low power
devices like sensors. It is quite useful as a general purpose protocol,
despite being small in scope.

Machine Head is a project for developers who want to integrate Clojure-based
services into a system that involves telemetry devices and would prefer
to keep the same protocol across the system. So it's not a replacement
for Langohr but a complimentary library. Indeed, [RabbitMQ 3.x supports MQTT](http://www.rabbitmq.com/mqtt.html)
so you can use both with it!


## Documentation and Examples

To get started with Machine Head, please refer to our [Getting Started guide](http://clojuremqtt.info/articles/getting_started.html). The rest of the documentation
is work in progress.

To give you a taste of what using Machine Head is like, here's a Hello, World
example:

``` clojure
(ns clojurewerkz.machine-head.examples.hello-world
  (:gen-class)
  (:require [clojurewerkz.machine-head.client :as mh]))

(defn -main
  [& args]
  (let [id   (mh/generate-id)
        conn (mh/connect "tcp://127.0.0.1:1883" id)]
    (mh/subscribe conn ["hello"] (fn [^String topic meta ^bytes payload]
                                   (println (String. payload "UTF-8"))
                                   (mh/disconnect conn)))
    (mh/publish conn "hello" "Hello, world")))
```


## Supported Clojure Versions

Machine Head targets Clojure 1.5+, tested against 3 Clojure versions x 2
JDKs on travis-ci.org, and is released under the Eclipse Public
License.


## Community

To subscribe for announcements of releases, important changes and so
on, please follow [@ClojureWerkz](https://twitter.com/#!/clojurewerkz)
on Twitter.



## License

The source is available [on
GitHub](http://github.com/clojurewerkz/machine_head). We also use
GitHub to track issues.


The [ClojureWerkz](http://clojurewerkz.org) Team
