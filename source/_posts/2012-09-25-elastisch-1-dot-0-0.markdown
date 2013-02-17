---
layout: post
title: "Elastisch 1.0: a minimalistic, well documented Clojure client for ElasticSearch"
date: 2012-09-26 14:45
comments: true
categories:
  - releases
  - elastisch
---

[Elastisch](http://clojureelasticsearch.info) `1.0` is here!

## TL;DR

Elastisch `1.0` is a battle tested minimalistic feature rich and well documented client for ElasticSearch.
It supports virtually every Elastic Search feature and has [solid documentation](http://clojureelasticsearch.info) that covers Elastic Search
and Lucene concepts and terminology as well as the actual library.

After 10 months of work, several alphas, betas and two RCs, Elastisch is ready to go `1.0`.



## What's In The Box

Here's what Elastisch supports out of the box:

 * Complete support for indexing operations
 * (Almost) complete support for querying, with the exception of multi-search
 * Support for all the query and filter types
 * Straightforward and consistent API that closely follows ElasticSearch REST API
 * [Solid documentation](http://clojureelasticsearch.info) (our favorite feature)
 * Facets (faceted search)
 * Percolation support
 * Administrative operations on indexes

To our knowledge, the only feature Elastisch does not support yet is multi-search, which is used relatively rarely. Minimalistic does not have
to mean primitive: Elastic Search has *many* features and Elastisch users should be able to easily benefit from them.

Learn more in the [Getting Started guide](http://clojureelasticsearch.info/articles/getting_started.html) and the rest of [the docs](http://clojureelasticsearch.info/).


## Documentation

Solid documentation is one of the goals of [ClojureWerkz libraries](http://clojurewerkz.org) and Elastisch is no exception. We believe that documentation
guides are more important than API reference because they are useful to people with all levels of expertise. Elastic Search's
own documentation is not bad but very reference-oriented. So for Elastisch, we took extra time to delay the 1.0 release and write
more detailed guides that introduce you to concepts, terminology, the analysis process, many query types and other numerous features Elastic Search
has:

 * [Getting Started guide](http://clojureelasticsearch.info/articles/getting_started.html) is a typical Getting Started guide with brief introductions, code examples and links to documents that provide more information.
 * [Mapping and Indexing guide](http://clojureelasticsearch.info/articles/indexing.html) covers many topics related to indexing, analysis, analyzers, mapping types
 * [Querying guide](http://clojureelasticsearch.info/articles/querying.html) covers querying, types of queries, filters, and so on
 * [Facets guide](http://clojureelasticsearch.info/articles/facets.html) covers faceted search, what it is good for, what Elastic Search has to offer and how to use it with Elastisch
 * [Percolation guide](http://clojureelasticsearch.info/articles/percolation.html) covers many things related to percolation

We hope this content will be useful as an intro to Elastic Search concepts for developers working in languages other than Clojure and eventually
can be used for Elastic Search's own doc guides.

We would like to thank [Karel Minarik](https://github.com/karmi) (the author of Tire) for proof-reading early versions of the guides and [Clinton Gormeley](https://github.com/clintongormley)
for [Elastic::Model](http://search.cpan.org/dist/Elastic-Model/) docs that we secretly have been stealing bits and ideas from. The Elastic Search community
is very nice and the feedback from other client library maintainers helped us improve Elastisch a lot.


## Development, Issue Tracking, Supported Clojure Versions

Elastisch targets Clojure 1.3+ and tested against 3 Clojure versions (`1.4`, `1.3`, `1.5-master-SNAPSHOT`) x 3 JDKs on travis-ci.org.

The source is available [on GitHub](http://github.com/clojurewerkz/elastisch). We also use GitHub to track issues. If you want to
contribute, there is a section on our workflow [in the README](https://github.com/clojurewerkz/elastisch/blob/master/README.md#development).


## License

Elastisch is released under the Eclipse Public License, the same as Clojure.


## News and Updates

New releases and updates are announced [on Twitter](http://twitter.com/clojurewerkz). Elastisch also has [a mailing list](https://groups.google.com/group/clojure-elasticsearch),
feel free to ask questions and report issues there.


## Elastisch is a ClojureWerkz Project

Elastisch is part of the [group of libraries known as ClojureWerkz](http://clojurewerkz.org), together with

 * [Welle](http://clojureriak.info), a Riak client with batteries included
 * [Monger](http://clojuremongodb.info), a Clojure MongoDB client for a more civilized age
 * [Neocons](http://clojureneo4j.info), a client for the Neo4J REST API
 * [Langohr](http://clojurerabbitmq.info), a Clojure client for RabbitMQ that embraces the AMQP 0.9.1 model
 * [Quartzite](http://clojurequartz.info), a powerful scheduling library

and several others. If you like Elastisch, you may also like [our other projects](http://clojurewerkz.org).

Let us know what you think [on Twitter](http://twitter.com/clojurewerkz) or on the [Clojure mailing list](https://groups.google.com/group/clojure).


The [ClojureWerkz](http://clojurewerkz.org) Team
