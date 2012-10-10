---
layout: post
title: "Announcing a new Clojure documentation project"
date: 2012-10-10 18:30
comments: false
categories: documentation, clojure
---

This blog is about [ClojureWerkz](http://clojurewerkz.org) libraries news and developments but this blog post is about
something else. Something more important, actually.

## TL;DR

Several community members are working on a [new Clojure documentation site](http://clojure-doc.org) that looks to improve the situation around
Clojure documentation and in particular make contributing documentation significantly easier:

 * [Hosted on GitHub](http://github.com/clojuredocs/cds)
 * Is not covered by the Clojure Contributor Agreement
 * Written in Markdown
 * Provides tutorials and in-depth guides on language features
 * Covers the ecosystem: libraries, tooling, development practices


## Announcing Community-Driven Clojure Documentation Site (CDS)

As communities around open source technologies grow, they hit road bumps every now and then.
For Clojure, the main limiting factor right now is documentation. This is suggested by both the data
from the most recent [The State of Clojure survey](http://cemerick.com/2012/08/06/results-of-the-2012-state-of-clojure-survey/) 
and the general community sentiment.

Current Clojure documentation is in bad shape primarily because there are no documentation guides. It's fair to say that
[clojure.org](http://clojure.org) is useless to beginners. To add insult to injury, the current Clojure Contributor Agreement process make it
impossible to contribute documentation or any content to clojure.org without first *mailing a piece of paper to USA*.

A few community members thought it does not have to be this broken and decided to start a new, completely community-driven
documentation site. It has an uninventive name, Clojure Documentation Site (CDS) and available at [clojure-doc.org](http://clojure-doc.org).

Next lets take a look at what the goals are and how it will be different from the broken system Clojure has in place today.


## How It Works

We have [a repository on GitHub](http://github.com/clojuredocs/cds) that has Markdown files, toolchain setup instructions and several articles
as well as stubs for several more articles. The stubs help contributors pick a topic to write about and not worry too much about
article structure initially. Just pick something that you are very familiar with or interested in and write.

When you are done, submit a pull request on GitHub and someone from the existing contributors team will
suggest improvements or merge your work. Pretty straightforward.



## What CDS Covers

CDS' goal is to cover more than just the language. It is certainly cruicially important to have good tutorials and comprehensive
guides on Clojure. But when using Clojure in real world projects, you will need to know about the JVM ecosystem, Leiningen,
how to write tests, what libraries are out there, how to profile code, JVM tooling for ops, how to develop and distribute libraires,
and much more.

So there is group of articles about "the Ecosystem stuff": think Leiningen, popular libraries or how to use VisualVM to find
hot spots and investigate concurrency hazards in your apps.

This means that if you feel that documenting sequences is boring but excited about the ops side of software engineering, you
can still contribute to CDS and enjoy the process.

When documenting various tools, sometimes it makes more sense to just link to existing documentation, which is what we 
do for Leiningen.



## What We Have So Far

CDS is a *very* young project (less than two weeks old) but we already have some content written by the core team
and community contributors:

 * [Getting Started tutorial](http://clojure-doc.org/articles/tutorials/getting_started.html)
 * [Intro to Clojure](http://clojure-doc.org/articles/tutorials/introduction.html)
 * A guide on [Clojure functions](http://clojure-doc.org/articles/language/functions.html)
 * A guide on [Java interoperability](http://clojure-doc.org/articles/language/interop.html)
 * A guide on [Polymorphism in Clojure](http://clojure-doc.org/articles/language/polymorphism.html)
 * A guide on the [Clojure community](http://clojure-doc.org/articles/ecosystem/community.html)
 * (Curated, opinionated, not comprehensive) [Clojure libraries directory](http://clojure-doc.org/articles/ecosystem/libraries_directory.html)



## Call to Arms

If your company uses Clojure or has interest in adopting it and has "open source Fridays", "hacker time" or something
similar, consider contributing to CDS. This will literally benefit the entire Clojure community, all the current and future users.

Not only every single Clojure user benefits from better documentation, it also gets outdated way slower than much of open source
code out there. In our opinion, contributing documentation for a programming language is one of the best ways to invest of
your OSS time budget.

No contribution is too small: feel free to suggest grammar improvements, better code examples, submit pull requests with just
one new paragraph or even a couple of spelling corrections. Editing and proof-reading is also a great way to contribute.

If you have design and/or frontend development skills, you are more than welcome to make CDS more legible, easy to navigate,
and simply better looking.

### But It Takes Forever/I'm Not A Good Writer/[Insert Your Excuse Here]

If you need examples of what's possible, here's what 2 ClojureWerkz core team members
could produce in about 6 months in their spare time:

 * [Monger documentation](http://clojuremongodb.info)
 * [Neocons documentation](http://clojureneo4j.info)
 * [Welle documentation](http://clojureriak.info)
 * [Elastisch documentation](http://clojureelasticsearch.info)
 * [Langohr documentation](http://clojurerabbitmq.info)
 * [Quartzite documentation](http://clojurequartz.info)

Both ClojureWerkz core team members are not native English speakers. Everybody can help. Imagine what Clojure
documentation may look like in a few months if CDS accumulates 10-15 active contributors and about as many
proof-reading content.


## Low-hanging Fruits

There are currently several articles that already have their structure in place, what is left is writing the content and code
examples. For example, you don't have to be a genius or a Clojure expert to write articles about

 * Books
 * [Java interop](http://clojure-doc.org/articles/language/interop.html)
 * [Collections and Sequences](http://clojure-doc.org/articles/language/sequences.html)
 * [Namespaces](http://clojure-doc.org/articles/language/namespaces.html)

If you want to start working on one of those articles or have existing content you've authored that can be ported,
please let us know on the [Clojure mailing list](https://groups.google.com/group/clojure).



## What CDS is Not

CDS does not try to cover API reference. [clojuredocs.org](http://clojuredocs.org) covers that pretty well already.


## Wrapping Up

Clojure documentation is the limiting factor for community growth. The existing contribution process is inadequate
for documentation. This led a group of community members to start a new project, with as low a barrier to entry as
possible. We already have some results to show and looking for your help!
