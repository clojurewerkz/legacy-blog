---
layout: post
title: "Clojure documentation project progress report: the week of October 14th"
date: 2012-10-15 12:00
comments: false
categories:
  - documentation
  - clojure
---

## TL;DR

The [Clojure documentation project](http://clojure-doc.org) started off quite actively. With several new guides and a dozen of contributors,
the resource is already quite useful to newcomers to the language. We believe this is directly related
to our straightforward contribution process.


## CDS Progress Report

A week ago we announced the new [Clojure Documentation Site](http://clojure-doc.org) (a.k.a. CDS) effort. The level of activity
in the first week exceeded our expectations and we thought it may be a good idea to publish periodic reports
(every week or two) to give the Clojure community a better idea of what CDS shapes up to be and what it has to offer.

So lets start. This is a report for the week ending October 14th, 2012.


## In a Gist

In the first week of CDS, we have added

 * 2 new tutorials and 5 new and 2 expanded guides
 * About 4,000 lines of changes in the content directory (does not include CSS or toolchain-related changes)
 * 14 merged pull requests
 * 13 contributors
 * About 1,400 unique visitors
 * About 6,000 page views with average visit duration of 2 minutes and 10 seconds

In addition, we have ironed out first issues in the contribution process and set up an IRC channel (`#clojure-doc` on `irc.freenode.net`) when
contributors coordinate their work.


## New Content

New tutorials:

 * [Emacs for Clojure development](http://clojure-doc.org/articles/tutorials/emacs.html)
 * [Eclipse and Counterclockwise for Clojure development](http://clojure-doc.org/articles/tutorials/eclipse.html)


New guides:

 * [clojure.core Overview](http://clojure-doc.org/articles/language/core_overview.html)
 * [Interoperability with Java](http://clojure-doc.org/articles/language/interop.html)
 * [Namespaces](http://clojure-doc.org/articles/language/namespaces.html)
 * [Polymorphism: Protocols and Multimethods](http://clojure-doc.org/articles/language/polymorphism.html)
 * [Collections and Sequences](http://clojure-doc.org/articles/language/collections_and_sequences.html)


## Updates

Improved guides:

 * [Functions](http://clojure-doc.org/articles/language/functions.html)
 * [Curated Clojure Library Directory](http://clojure-doc.org/articles/ecosystem/libraries_directory.html)


## Thank You, Contributors

CDS would not be possible without the following people who make Clojure community a better place:

 * Gareth Jones
 * John Gabriele
 * Claudio Perez Gamayo
 * gsnewmark
 * Phil Hagelberg
 * Lee Hinman
 * Michael Klishin
 * Julson Lim
 * Jake McCrary
 * Max Penet
 * Oleksandr Petrov
 * Robert Randolph
 * Yogthos


## You Can Help!

### How It Works

We have [a repository on GitHub](http://github.com/clojuredocs/cds) that has Markdown files, toolchain setup instructions and several articles
as well as stubs for several more articles. The stubs help contributors pick a topic to write about and not worry too much about
article structure initially. Just pick something that you are very familiar with or interested in and write.

When you are done, submit a pull request on GitHub and someone from the existing contributors team will
suggest improvements or merge your work. Pretty straightforward.

In order to make it easier for potential contributors to join the project, we will post a brief list of
guides that do not require deep expertise and can benefit from contributions by complete beginners.

### Existing Guides

Tutorials that need work:

 * [Tutorial on VimClojure](http://clojure-doc.org/articles/tutorials/vim.html)


Guides that have structure and good chunk of the content in place but still have many holes you
can help us plug:

 * [clojure.core Overview](http://clojure-doc.org/articles/language/core_overview.html)
 * [Java interop](http://clojure-doc.org/articles/language/interop.html)
 * [Collections and Sequences](http://clojure-doc.org/articles/language/sequences.html)
 * [Namespaces](http://clojure-doc.org/articles/language/namespaces.html)

### New Content

If you want to start working on one of those articles or have existing content you've authored that can be ported,
please let us know on the [Clojure mailing list](https://groups.google.com/group/clojure).

### But It Takes Forever/I'm Not A Good Writer/[Insert Your Excuse Here]

If you need examples of what's possible, here's what 2 ClojureWerkz core team members
could produce in about 6 months in their spare time:

 * [Monger documentation](http://clojuremongodb.info)
 * [Neocons documentation](http://clojureneo4j.info)
 * [Welle documentation](http://clojureriak.info)
 * [Elastisch documentation](http://clojureelasticsearch.info)
 * [Langohr documentation](http://clojurerabbitmq.info)
 * [Quartzite documentation](http://clojurequartz.info)

Both ClojureWerkz core team members are not native English speakers. You certainly can contribute even if
you allocate 30 minutes per week for it.


## Other Ecosystem Documentation Improvements

CDS is about improving Clojure documentation all around the spectrum: from tutorials to language guides
to documentation about important parts of the ecosystem. One of the fundamental building blocks
of the Clojure ecosystem is [Leiningen](http://leiningen.org). There were two improvements to
Leiningen documentation this week:

 * The [Leiningen tutorial](https://github.com/technomancy/leiningen/blob/master/doc/TUTORIAL.md) got an update
 * A new guide was added: [Managing Polyglot (e.g. Clojure/Java) Projects with Leiningen 2](https://github.com/technomancy/leiningen/blob/master/doc/MIXED_PROJECTS.md)


## Summary

CDS is shaping up quite nicely. With over a dozen of contributors and 8 piece of content contributed the first week,
the progress has exceeded our expectations. The Clojure community still has *very* long way to go with respect to
documentation but this is encouraging.

And, [you can help](http://github.com/clojuredocs/cds)!


On behalf of the [Clojure Documentation Team](http://github.com/clojuredocs)
