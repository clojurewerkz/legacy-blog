---
layout: post
title: "How to Make Your Open Source Project Really Awesome, Part 2"
date: 2014-07-20 17:01:20 +0400
comments: false
categories:
  - misc
---

## TL;DR

This is a continuation to [How to Make Your Open Source Project Really Awesome](http://blog.clojurewerkz.org/blog/2013/04/20/how-to-make-your-open-source-project-really-awesome/).

In addition to the things recommended in the first part, do the following:

 * Talk to your biggest users
 * Make it easy to contribute
 * Publish releases often


## How To Make Your Open Source Project Really Awesome, Part 2

As ClojureWerkz approaches its 3rd birthday, it's time to expand our (relatively)
popular blog post from early 2013, [How to Make Your Open Source Project Really Awesome](http://blog.clojurewerkz.org/blog/2013/04/20/how-to-make-your-open-source-project-really-awesome/).

The focus of this part is on how to help your users help you, the maintainer. Very
few successful open source projects are one man shows. The more people contribute,
the better the project can get and less time it will take on your end to maintain
it well.

## Talk to Your Biggest Users

If your project is reasonably licensed and you maintain it well, eventually there will be
people using it in commercial software. Some of them will be one man shops, others are
giant public corporations. Most will lie in-between. It's still possible to identify
some key users: those that really push your project to the limits. Their engineers
will be filing the most issues, will turn up on your mailing list more often than
others, etc.

You need to identify those users and talk to them. Ask them what they do and don't like,
what they find missing, why they decided to use your project over an alternative.

Not only this kind of feedback is the best roadmap for your project, you will build
some connections along the way. With ClojureWerkz, we are very fortunate to have
commercial users among the companies we admire. Not only that, we now know some of
their engineering team members. It's never a bad position to be in.


## Make It Easy to Contribute

We've touched on this in the [first part](http://blog.clojurewerkz.org/blog/2013/04/20/how-to-make-your-open-source-project-really-awesome/). Time to expand on this key subject
a little bit.

### Identify Low Hanging Fruit Issues

Most contributors start with small issues: contribute a documentation fix here, a tiny
feature there, a few extra failing test cases for this issue. Few of your users will
jump in and contribute a major feature from the get-go. There are fairly objective
reasons for this:

 * It takes time to get familiar with a codebase
 * People are more confident contributing to the projects where they "know" one of the maintainers
 * Contributing major features requires having some experience with the project

All of this takes time. Making it painless for your users to become contributors
is perhaps the most important thing you can do. Except for the smallest projects,
it usually separates the projects that will die from those that will march on even
if you, the author, completely lose interest or ability to work on it.

Here's a trick we've been trying with some of our projects (e.g. Elastisch): label
GitHub issues with `low-hanging fruit`. When someone asks how she can help you,
point the person to this label. We've seen this work very well for possibly the most
widely used Clojure project out there: [Leiningen](https://github.com/technomancy/leiningen).

At the time of writing, Leiningen has 217 contributors, which is not a small number
by any stretch (the most popular ClojureWerkz projects have something between 25 and 40).


### Document Development Setup

Many projects have some kind of development setup that needs to be performed before
you can work on it. It can be a database of some kind running locally, or an env
variable set to a particular value. For example, testing the [Elastisch](http://clojureelasticsearch.info) requires setting an env variable that tells the test suite what's the name
of the local ElasticSearch cluster should be.

On top of that, there can be multiple ways to run the tests, multiple test suites,
OS-specific hacks necessary, VM/compiler version requirements, etc.
Document as much of this process as you can. It should be dead obvious how to
set things up for development.

If you have a specific VCS workflow (e.g. development happens on the branch `devel` and
master is only used for stable releases), document this as well. Add a [CONTRIBUTING.md](https://github.com/blog/1184-contributing-guidelines)
file to the repo to make this more visible.

Not doing so will result in frustration for potential contributors. Don't know about
you but I'm not very motivated to contribute to a project that makes it frustrating.


### Don't Be an A-hole

This is a subject of a blog post of its own but be a decent person on the Internet
(yes, it's possible!). Be respectful. Point out various issues
in contributed pull request in a reasonably polite way.

Nobody ever will contribute to a project maintained by an a-hole.


## Publish Releases Often

This applies to both bug fix releases and development milestone
versions. For ClojureWerkz projects, we often publish a new bug fix
release when only 1 or 2 bugs were fixed. It's easy for us to do and
may save some pointless work for the users affected by the bugs.

With Leiningen, it takes a couple of commits (version changes) and 2
lines in the terminal to push a new release:

```
lein do pom, jar
scp push target/[jar] clojars@clojars.org:
```

With Leiningen 2.4, it can be as easy as [a single command, `lein release`](https://github.com/technomancy/leiningen/blob/master/doc/DEPLOY.md#releasing-simplified).

It is also an important thing to do for development milestones. Added
a couple of neat features to your project? Publish a new beta
release. There will be users who were dying to get their hands on this
feature, so much so that they're willing to run a beta in production
just to not spend days reinventing the wheel.

As always, state release stability clearly in the change log and
release notes.

This helps avoid another common mistake (applicable primarily to JVM languages):
forcing your users to use snapshot releases. Snapshot releases make repeatable
builds pretty much impossible and some tools (e.g. Leiningen) won't allow
non-snapshot releases depend on snapshot ones.

## Give Credit Where Due

It's always a good idea to give your contributors some credit by mentioning them in
the change log. Even better, have a "Thank You, Contributors" section in your
release announcement. Few things are as motivating as getting recognized for your
work.


## Final Thoughts

Just like it is not terribly hard to make your project approachable, it is also
not that hard to make it contributor-friendly. Having a healthy number of contributors
(even if it's just 2-4) ensures that the project will live on even if you no longer
have the time (or interest) maintain it.
For example, I have a project that I haven't contributed any code to since 2008. It is
still being used and improved by other people.

Maybe more importantly, making your project contributor-friendly will
introduce you to a lot of people and may open a lot of doors to you in
the software industry, at least in engineering.


## About the Author

[Michael](http://twitter.com/michaelklishin) on behalf of the ClojureWerkz team.
