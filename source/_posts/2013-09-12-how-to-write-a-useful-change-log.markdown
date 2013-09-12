---
layout: post
title: "How to Write a Useful Change Log for Your Open Source Project"
date: 2013-09-07 23:22
comments: false
categories:
  - misc
---

## TL;DR

A useful project change log answers three questions:

 * Whether it is critical to update
 * Whether the release is backwards compatible
 * What has changed and why

A change log that covers these three points will help your users adopt
new versions faster, even in some of the most conservative corporate environments.
It will also make the ops people respect your project more.


## Before We Start

Back in April we described some of the things [we think make an open source project awesome](http://blog.clojurewerkz.org/blog/2013/04/20/how-to-make-your-open-source-project-really-awesome/).

That blog post got a lot of positive responses. Today we will dig a
little deeper in one aspect of maintaining a project: writing a good
change log.

Before we start, let's remind a rule of thumb you can use with anything
related to open source:

> Don't make your users mad

also known as

> Don't make your users want to break the computer


## Bro, Do You Event Change log?

Besides documentation, which often takes a fairly substential amount of effort to write
well and edit, a good change log is (in our opinion) the second most important
thing that earns you credibility in your users' eyes.

Unfortunately, the majority of open source projects on GitHub do not
have a change log at all.


## How To Write a Good Change Log

Before we talk about how to maintain a good change log, let's define "good".
Good for a change log means informative. What kind of information a user
is looking for when she is looking to upgrade? This will vary from person
to person, but it likely includes a few things:

 * Is this release critical? Should I upgrade immediately or can it wait?
 * Is this release backwards compatible? Should I expect things to just work?
 * What has changed? Why? How can I use the new stuff?

All of these are very important for ops people, because when stuff
breaks, they get woken up late at night. But a good change log is not
written with just developers or just ops engineers in mind, it caters
to both.


## What Ops Care About

Like we've mentioned earlier, if an upgrade cases an outage, some
people may be woken up at night. If that happens more than once thanks
to your project, you can be damn sure that they will push for one of
two things:

 * That your project is not upgraded for as long as possible
 * That your project is avoided altogether

As a maintainer, these are some of the worst things that can happen.
So mess with ops people at your own risk. It won't take hours to
make them confident about upgrading, though. All you need to do is to
**make it clear if the release has any breaking changes**.

It's OK for your project to have breaking changes every once in a while.
Just make it very clear in the announcement and change log when it happens.

Then mention if it is a **critical upgrade or not**. Using [semantic
versioning](http://semver.org/) will help with this (major versions
are rarely critical but point releases may fix critical bugs or
security issues).

In some cases, a bug that you fix affects a lot of people. That should
be well reflected, too. In other cases it affects a tiny minority, people
who run a certain OpenBSD version on a rarely used hardware architecture,
or a specific patch release of a runtime. In such cases, mentioning
that the issue only affects such and such environments is a good idea
as it will make everybody else upgrade quicker.

A common case of major breaking changes that primarily concern ops
is when you drop support for a particular runtime version. For example,
we've started phasing our support for Clojure 1.3 for our projects
last month. Not mentioning such changes is basically stabbing your users
in the back.

### Example 1

[Langohr 1.5 change log](https://github.com/michaelklishin/langohr/blob/master/ChangeLog.md#changes-between-langohr-140-and-150) explicitly states that Clojure 1.3 is no longer
supported:

<script src="https://gist.github.com/michaelklishin/64f3c6efb24191bcc831.js"></script>

### Example 2

For [Cassaforte](http://clojurecassandra.info) `1.0.0-rc4` we decided we really need
to move some code around between namespaces. It sucked to break the API at such a late
stage but it was still in pre-`1.0` days so we decided to do it. We knew Cassaforte
already had a few users, so we mentioned the breaking changes in bold in the first
line of the change log for that release:

<script src="https://gist.github.com/michaelklishin/c93489b0d48fd2006e86.js"></script>

### Example 3

We don't always mention whether everyone should upgrade in change logs for
ClojureWerkz projects but I ([@michaelklishin](http://github.com/michaelklishin)) try to
do so for my other projects. We also mention this in release announcements.

In any case, if you know what group of users may be affected, mentioning that
will earn you bonus points.


### Summary

As you can see, **it does not take much effort to make it very clear that
there are breaking changes in a release**. In fact, it often takes a single line
of text. You can write that in a fraction of the time it takes you to skim
Hacker News front page. **No excuses**.


## What Developers Care About

Developers need a little more information from change logs. Sure, it's just as
important for them to know if there are breaking changes. But developers are
more concerned with what new features were introduced.

It's not sufficient, however, to just mention that there is a new feature
X available in the release. You need to make it easy to understand how to
use it. This means that documentation needs to be reasonably up-to-date
and that you need to provide some examples in the change log itself.

Below are some example from [Monger](http://clojuremongodb.info), [Langohr](http://clojurerabbitmq.info)
and other projects of ours.


### Example 1

<script src="https://gist.github.com/michaelklishin/2965840c1fb1f056548a.js"></script>

### Example 2

<script src="https://gist.github.com/michaelklishin/e3cf04c4fbaac82b2fbc.js"></script>

### Example 3

<script src="https://gist.github.com/michaelklishin/de81d53ac988576c1982.js"></script>


## How Not To Write a Change Log

Every once in a while you find a project that has `ChangeLog.md` in the repo that
basically says "see git log for change log".

Unless you write amazingly detailed commit messages and very carefully
merge topic branches, that is not a change log. That is a "screw you,
figure it out, I don't owe you anything" thrown to your users. Don't
be that guy.


## Final Thoughts

As you can see, it does not take a lot of effort to go from a useless change log
to something that will help your users and, in turn, your project adoption.



[Michael](http://twitter.com/michaelklishin).


