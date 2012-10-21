---
layout: post
title: "Clojure documentation project progress report, Oct 21th"
date: 2012-10-22 13:00
comments: true
categories:
  - documentation
  - clojure
---

## TL;DR

The [Clojure documentation project](http://clojure-doc.org) continues to progress nicely. Several guides
now have more than 2/3rds of the content written and the team begins to tackle harder guides such
as [Concurrency and Parallelism in Clojure](http://clojure-doc.org/articles/language/concurrency_and_parallelism.html).


## CDS Progress Report

Not so long we announced the new [Clojure Documentation
Site](http://clojure-doc.org) (a.k.a. CDS) effort.  Now we publish
periodic reports (every week so far, possibly two weeks in the future)
to give the Clojure community a better idea of what CDS shapes up to
be and what it has to offer.

This is a report for the week ending October 21st, 2012.


## Overview

This week was spent mostly refining and expanding the material we've added last week. This means
there are fewer commits and the diff is smaller but a lot more time went into reading and editing.

There was, however, some new content, too.


## New Content

This week we started working on the first out of 3 "advanced" guides:
[Concurrency and Parallelism in
Clojure](http://clojure-doc.org/articles/language/concurrency_and_parallelism.html).
It is a very broad topic, with lots of material to write and some
areas not-so-trivial to explain to absolute beginners.  At the same
time, it covers some of the key Clojure design decisions and some of
the most attractive points of the language, so we are happy to work
extra hard on this subject. And it's always good to review your own
understanding of concurrency by writing this content.


## Updates

A number of guides is getting pretty close to be considered "75% done":

 * [clojure.core Overview](http://clojure-doc.org/articles/language/core_overview.html)
 * [Interoperability with Java](http://clojure-doc.org/articles/language/interop.html)
 * [Namespaces](http://clojure-doc.org/articles/language/namespaces.html)
 * [Polymorphism: Protocols and Multimethods](http://clojure-doc.org/articles/language/polymorphism.html)
 * [Collections and Sequences](http://clojure-doc.org/articles/language/collections_and_sequences.html)



## Thank You, Contributors

CDS would not be possible without the following people who make Clojure community a better place:

 * Daniel Jomphe
 * Gareth Jones
 * John Gabriele
 * Lee Hinman
 * Michael S. Klishin
 * Robert Randolph


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

Guides that have structure and good chunk of the content in place but still have holes you
can help us plug:

 * [Java interop](http://clojure-doc.org/articles/language/interop.html)
 * [Collections and Sequences](http://clojure-doc.org/articles/language/sequences.html)
 * [Namespaces](http://clojure-doc.org/articles/language/namespaces.html)
 * [clojure.core Overview](http://clojure-doc.org/articles/language/core_overview.html)

These guides are new and cover advanced topics, so we need as much proof-reading as we can
get from the community:

 * [Concurrency and Parallelism in Clojure](http://clojure-doc.org/articles/language/concurrency_and_parallelism.html)

### New Content

If you want to start working on one of those articles or have existing content you've authored that can be ported,
please let us know on the [Clojure mailing list](https://groups.google.com/group/clojure).


## Summary

CDS is getting to the point of being a really useful resource to
newcomers. We still have a very long way to go before Clojure
documentation can be considered excellent but close enough to the
point when it can be recommended to newcomers without feeling bad
about it.

Want to help us make things better? [Join us](http://github.com/clojuredocs/cds)!


On behalf of the [Clojure Documentation Team](http://github.com/clojuredocs)
