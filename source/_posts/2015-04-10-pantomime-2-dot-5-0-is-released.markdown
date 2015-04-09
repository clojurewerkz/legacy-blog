---
layout: post
title: "Pantomime 2.5.0 is Released"
date: 2015-04-10 00:33:39 +0300
comments: false
categories:
  - pantomime
  - releases
---

## TL;DR

[Pantomime](http://github.com/michaelklishin/pantomime) is a Clojure interface to Apache Tika.


## Changes between Pantomime 2.4.0 and 2.5.0

### Content Extraction API

Pantomime now provdes access to Tika's content extraction
functionality via `pantomime.extract/parse`:

``` clojure
(require [clojure.java.io :as io]
         [pantomime.extract :as extract])

(pprint (extract/parse "test/resources/pdf/qrl.pdf"))

;= {:producer ("GNU Ghostscript 7.05"),
;=  :pdf:pdfversion ("1.2"),
;=  :dc:title ("main.dvi"),
;=  :dc:format ("application/pdf; version=1.2"),
;=  :xmp:creatortool ("dvips(k) 5.86 Copyright 1999 Radical Eye Software"),
;=  :pdf:encrypted ("false"),
;=  ...
;=  :text "\nQuickly Reacquirable Locks∗\n\nDave Dice Mark Moir ... "
;= }
```

If extraction fails, `extract.parse` will return the following:

``` clojure
{:text "",
 :content-type ("application/octet-stream"),
 :x-parsed-by ("org.apache.tika.parser.EmptyParser")}
```

`extract/parse` is a simple interface to Tika's own
[Parser.parse method](https://tika.apache.org/1.7/parser.html).

Contributed by Joshua Thayer.



## Change Log

[Pantomime change log](https://github.com/michaelklishin/pantomime/blob/master/ChangeLog.md) is available on GitHub.



## Pantomime is a ClojureWerkz Project

[Pantomime](http://github.com/michaelklishin/pantomime) is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Elastisch](http://clojureelasticsearch.info), a minimalistic Clojure client for ElasticSearch
 * [Cassaforte](http://clojurecassandra.info), a Clojure Cassandra client built around CQL
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Pantomime, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team
