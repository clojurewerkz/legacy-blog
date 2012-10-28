---
layout: post
title: "Clojure documentation project progress report: the week of October 28th"
date: 2012-10-29 00:56
comments: false
categories: 
  - documentation
  - clojure
---

## TL;DR

The [Clojure documentation project](http://clojure-doc.org) continues to make progress.
Lion's share of the work this week went into the [Concurrency and Parallelism in Clojure](http://clojure-doc.org/articles/language/concurrency_and_parallelism.html)
guide which is now about 75% complete.


## CDS Progress Report

The [Clojure Documentation
Site](http://clojure-doc.org) (a.k.a. CDS) publishes
periodic reports (every week so far, possibly two weeks in the future)
to give the Clojure community a better idea of what CDS shapes up to
be and what it has to offer.

This is a report for the week ending October 28st, 2012.


## New Content

This week was all improvements to existing guides, no new content merged. There is at least one new tutorial
in the works by a contributor we've heard from, though.


## Updates

By far most of the work merged this week went into the [Concurrency and Parallelism guide](http://clojure-doc.org/articles/language/concurrency_and_parallelism.html).

It now covers topics such as

 * An overview of concurrency terminology and common hazards
 * Identity/Value separation in Clojure
 * atoms
 * agents
 * refs
 * vars
 * delays
 * futures
 * promises
 * dereferencing
 * some commonly used `java.util.concurrent` bits
 * other approaches to concurrency on the JVM available to Clojure through libraries

Language-level support for concurrent programming is one of the Clojure's design goals so reading that guide
is highly recommended.


Tutorials updated this week:

 * [Getting Started With Emacs for Clojure](http://clojure-doc.org/articles/tutorials/emacs.html)

Other guides updated this week:

 * [Functions](http://clojure-doc.org/articles/language/functions.html)
 * [clojure.core Overview](http://clojure-doc.org/articles/language/core_overview.html)
 * [Interoperability with Java](http://clojure-doc.org/articles/language/interop.html)
 * [Community](http://clojure-doc.org/articles/ecosystem/community.html)



## Thank You, Contributors

CDS would not be possible without the following people who make Clojure community a better place:

 * AtKaaZ
 * Ben Poweski
 * John Gabriele
 * Lee Hinman
 * Michael S. Klishin
 * Wes Freeman


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

CDS is 2-3 guides from covering the language "reasonably well". There still are holes in various guides
but mostly in the more advanced areas and expectedly will take longer to write.

Want to help us make things better? [Join us](http://github.com/clojuredocs/cds)!


[Michael Klishin](http://twitter.com/michaelklishin) on behalf of the [Clojure Documentation Team](http://github.com/clojuredocs).
