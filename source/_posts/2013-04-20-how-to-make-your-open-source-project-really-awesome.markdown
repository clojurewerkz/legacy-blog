---
layout: post
title: "How To Make Your Open Source Project Really Awesome"
date: 2013-04-20 01:00
comments: false
categories:
  - misc
---

## TL;DR

If you plan on releasing a library as open source, please make sure it has

 * Clear dependency/installation instructions
 * At least one brief documentation guide
 * A change log and tags in the repo
 * Some information about supported language/runtime/tool versions and project maturity
 * A mailing list where users can ask questions and help each other

Doing anything less than this will cause some of your users grief and anger.
And likely some wasted time.


## How To Make Your Open Source Library Really Awesome

Year after year, more and more people release libraries they've
developed and would like to open source. Today we'd like to share a little bit
of our experience about how to make sure users of your library are content
with it.

There is one Rule of Thumb to this:

> Don't make your users mad

also known as

> Don't make your users want to break the computer

now lets see how specifically we can achieve that goal with a reasonable
amount of effort.



## Give It a Really Useful README

Even if your project has a nice site, it is likely that the first point of contact
of potential users with it will be by reading the README file. We need to make
sure it is awesome and contains useful information.

### Provide Dependency Information

So you release open source software. This probably means you are kinda smart. Good
for you. Unfortunately, not everybody is and some people are completely new to the
Clojure ecosystem. This means that what is obvious to you is not at all obvious
to many other people.

One such thing is missing dependency/installation information.

> How do I even install this, was it so hard to make this clear?

is something that quickly leads to anger. Digging in the source to find
our your artifact/gem/package name is annoying and some projects use really
creative (read: stupid) names for artifacts that do not match code repository
name, etc.

Relieve your users from having to deal with this crap. Make it dead obvious
how to add a dependency on your project, ideally by copy-pasting a snippet.


### State Project Maturity Clearly

Have you been using it in production for months? Is it something you still believe
is incomplete? Do you expect the API change drastically in the next version? Is this
project mature and safe to use even for the most demanding and conservative projects?

State all that clearly. And next time you won't waste a week of your time because
you've made the wrong call on a library that did not provide any maturity information,
you will realize how much difference a few sentences can make to real people.

### Document Supported Runtime/Language/Tool Versions

Clojure has a very good track record when it comes to backwards compatibility. It is almost
too good to be true. Besides the `1.2` to `1.3` migration, subsequent releases are pretty
much a drop-in replacement for the vast majority of projects out there. As such, projects
that have moved beyond `1.2` are generally on the most recent stable release

However, this won't always be the case. At some point, a future Clojure release
will have to break compatibility. How do we not make our users furious? By clearly
stating what versions are supported in the README.

All it takes is writing one line of text. One less tweet on the week of your release
and you save beginners potentially a lot of head scratching.

If you need an example, [here's one from Welle](https://github.com/michaelklishin/welle#supported-clojure-versions).



### State What License You Use

You may not care about licenses much, but people who want to use your library at a BigBucks Inc do.
They must know. And it may be a deal breaker for them when they want to adopt Clojure/Node.js/Scala/Go/whatever.

So state your license clearly. And please, use something business-friendly unless you have good reasons.
Apache Public License 2.0, Eclipse Public License and MIT are three good, friendly choices.

Finally, remember that you can double-license, e.g. APL2/MIT/GPLv2 if you really want to be license-neutral.
Then your users will pick what suits them.


### How To Fuck It Up

If you want to completely screw your users, do this:

 * Put a nearly blank README to your project's root
 * Make it say "patches welcome" at the end
 * Invent your own license or use a completely unfamiliar one, such as [WTFPL](http://en.wikipedia.org/wiki/WTFPL)

Then your project will never have any users. Guaranteed.




## Document Your Project

Documenting things is not easy and can be time consuming. However, documentation is the single
best thing you can do to your users. Not only it saves them *a lot* of time, it makes them
confident that your library is not abandonware.

Documentation helps your users accomplish things they decided to use your library in the first
place. In the words of Rob Pike, it "empowers them". It shows them that you care. It shows
them that you are a real person, not a robot spitting code.

After about 2 years of working on [ClojureWerkz](http://clojurewerkz.org), I can confidently
say that there is nothing our users love our stuff more than solid documentation:

 * [Elastisch documentation](http://clojureelasticsearch.info)
 * [Welle documentation](http://clojureriak.info)
 * [Neocons documentation](http://clojureneo4j.info)
 * [Monger documentation](http://clojuremongodb.info)
 * [Langohr documentation](http://clojurerabbitmq.info)

[Writing great documentation](http://jacobian.org/writing/great-documentation/) takes time.
Fortunately, modern tooling also helps you quite a bit and reduces the annoyances you have
to deal with by a lot.

For ClojureWerkz projects, we've open sourced our [Jekyll-based documentation site template](https://github.com/clojurewerkz/docslate).
We are not great at CSS and the visual aspect of design, so we use Twitter Bootstrap. While
our doc sites could look better, it is certainly pretty good compared to most open source
projects out there. And you can use our template or create a similar one for your projects.

Better yet, if you open source your documentation site (and there is no reason to not do so),
you will likely see people contributing minor improvements and corrections earlier than they will
contribute code changes.

If you are still not sure whether documenting your project is worth it, watch this talk
by Jacob Kaplan-Moss:

<iframe src="http://blip.tv/play/g4VigquCRgI.x?p=1" width="720" height="433" frameborder="0" allowfullscreen></iframe><embed type="application/x-shockwave-flash" src="http://a.blip.tv/api.swf#g4VigquCRgI" style="display:none"></embed>


### How To Fuck It Up

If you want to completely screw your users, do this:

 * Don't write a single documentation guide, not even one example
 * Make sure your API reference is outdated by at least 3 months
 * Claim that people who are not willing to read the code to figure out even the most basic things are stupid and should flip burgers instead



## Make It Easy to Upgrade

At some point, you are going to make another release of your project. This is another opportunity
to either make your users happy that they've gone with your library or make them furious and
waste their time.

### Give a Fuck About Backwards Compatibility

One of the most infuriating things about software development is that moment when you upgrade a library
and hundreds of tests fail. The only thing that angers me more is when I also have to rewrite half
of my codebase because someone somewhere decided that breaking the public API without warning
is fine.

So, commit to maintaining backwards compatibility. Of course, you don't have to support projects
from 15 years ago like OpenJDK does. But deprecate things before removing them and make it easy
to discover what has changed.

How do you do that? By keeping a change log.


### Have a Change Log

Every once in a while, your users will upgrade (more on this later in this post). The main
questions they are going to ask themselves is

> What has changed in this release?

and then

> Will my code break? Will I have to rewrite it?

and finally,

> Will Joe the ops guy hate me for upgrading?

All of these can be answered by having a *change log*. It's like Twitter except it's actually
useful. Here's how it works:

 * Every time you fix a bug, you write a brief entry to the change log
 * Every time you add a feature, you briefly mentoin it in the change log with a few code examples
 * Every time you make a breaking API change, you clearly state that **in bold** in the change log

That's it. There is no step 3.

Change logs typically use reverse chronological order. Changes are grouped by versions. If you have
multiple branches (e.g. `master` and `1.0.x`), each one has a separate change log.

That is all. For example, here's an [example from Welle](https://github.com/michaelklishin/welle/blob/master/ChangeLog.md).



### Tag Releases

It's that time again. You've bumped the version and about to publish artifacts. Stop and make
another thing first: tag the commit that changes the version. Without tags it will be
a royal pain to come up with a diff betwee nversions.

Some dependency (e.g. Bundler, Rebar) and configuration management tools can use tags
and developers will expect tags to be available.

Use a consistent version scheme, e.g. `v1.0.0-alpha1`, `v1.0.0`, `v1.1.2`, etc. Having
inconsistent tag names will guaratee ops people will hate your project till the end
of days.


### Announce Releases

Next thing to do after you announce a release is to write a blog post or simply a
post to the mailing list of your project or a larger relevant mailing list
(e.g. [Clojure mailing list](https://groups.google.com/group/clojure) or [RabbitMQ Discuss](https://lists.rabbitmq.com/cgi-bin/mailman/listinfo/rabbitmq-discuss)).

Make sure the title starts with `ANN` or `[ANN]` to indicate that it is an announcement,
e.g.

> ANN Welle 1.5.0 is released

In your announcement make it clear what the project does
and if the release is backwards-compatible or not, and link to the change log
where users can find more details. That's it.

### Use Preview/Snapshot Versions For Development

Ever saw a project that has the same version, e.g. `0.2.1`, for half a year? How do you
know which version is actually `0.2.1`? Is it a version in development? Did someone forget
to bump it after a release? What's going on?

This is driving all developers crazy. Don't be that person. Use preview/snapshot
versions for development and only "seal" versions when you are about to tag and cut
a release. Then **immediately** bump the version to development.

Examples of development versions:

 * `1.1.0.pre1`
 * `1.1.0-alpha1`
 * `1.1.0-SNAPSHOT` (for JVM languages)


Any other version naming scheme is confusing and will guarantee your users a bad time.


### How To Fuck It Up

If you want to completely screw your users, do this:

 * Break your public API randomly, ideally in subtle ways that your test suite won't even reveal
 * Forget to bump development version
 * Never tag releases
 * Never announce releases




## Use GitHub

I have no affiliation with GitHub and don't assume Git is "the best" version
control system out there. But it's pretty good. And nearly everybody is
on GitHub these days.

GitHub makes several things easy:

 * Discover your project
 * Browse and search code
 * Bring your attention to issues by filing issues or @mentioning you
 * Contribute trivial changes

Maybe the most importantly, **GitHub is pretty friendly to less technical people**. Yes, it is,
and they are working hard on making it even better.

Using GitHub means you'll have an extremely easy to use CI service: [Travis CI](http://travis-ci.org).

You will get a lot more admiration from your users if you won't make their life
harder by asking them to deal with patches, look for your email across the
Web to report issues and clone your 300 MB repository over poor 3G just to edit
one typo.

<blockquote class="twitter-tweet" lang="es"><p>@<a href="https://twitter.com/old_sound">old_sound</a> @<a href="https://twitter.com/g3rtm">g3rtm</a> bitbucket is a good service, no doubt. But people who choose it for public code are just being difficult (according to me)</p>&mdash; Michael Klishin (@michaelklishin) <a href="https://twitter.com/michaelklishin/status/293485697262833664">21 de enero de 2013</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

Don't be difficult.


## Have a Place Where Users Can Get Support

If your project reaches any reasonable kind of popularity, you will have to answer questions
about it. For that, set up a mailing list (a Google group will do) and if you frequent
on IRC, start a channel.

Think you don't have any time? The best part about having a mailing list is that users will
quickly start helping themselves if you give them a way. So clearly indicate ways to get
support in your project's README.

Search Twitter for the name of your project every so often. You will discover all kinds
of questions, criticism and praises. If you use Twitter actively, start a separate
account for your project, like we have done with [@ClojureWerkz](http://twitter.com/clojurewerkz).

It will help you build a community, learn about how people use your project and what can
be improved. Finally, it will help you find people who will be able to help maintain
your project. Not only it will save you time, it will encourage those people to spread
the word about it.

### How To Fuck It Up

If you want to completely screw your users, do this:

 * Be hip and disable issues on your GitHub repository
 * Use a contributor agreement users have to mail in paper to Tanzania
 * Insist on using patches even for one line changes to the README
 * Put your repo into Darcs even if it's a Ruby or JavaScript or Clojure project
 * Make it hard to find where the repository is

This will prevents others from contributing to your project and stealing some of the credit
from you.



## Pass It Over

At some point you may become disinterested in maintaining your project. Maybe you've moved
on to a new job or no longer use your own project. Announce it on the mailing list,
ask someone to take over your project. Sooner or later, someone will help.
Being on GitHub helps with this, especially after they've introducted a feature
that lets you transfer repository ownership.

No matter what you do, don't turn your project into abandonware. This is the most
sure way to want your current and future users to go on a kitten killing spree.

It's always better to pass the project on than to make excuses later.


### How To Fuck It Up

If you want to completely screw your users, do this:

 * Simply stop contributing to your project and answering mailing list questions without any explanation
 * Ignore pull requests, claim they should be called something else and are not really useful
 * Claim you simply are a Get Shit Done guy who loses interest once the problem is done

This will make sure your project will eventually be forked at least 300 times and an alternative
will be created because figuring out which fork has what bugs fixed will be too annoying.



## Final Thoughts

As you can see, it is not that hard to make your project approachable. Besides documentation guides, it does not
take much to make sure your users are not mad and ops people don't hate you.

Maintaining open source projects takes time and effort. But it pays off. I've been
[on GitHub](https://github.com/michaelklishin) since beta and can say that few other things have brought me more professional
opportunities I'm blessed to have today than being active in the open source
community.

And if you are not going to make something awesome, maybe better don't release it
in the first place.

[Michael](http://twitter.com/michaelklishin).
