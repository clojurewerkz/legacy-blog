---
layout: post
title: "How We Document Our Projects with ClojureWerkz Docslate"
date: 2013-06-15 15:18
comments: false
categories:
  - misc
  - documentation
---

This post will explain how our team was able to greatly reduce the
friction in writing documentation guides by standardizing on
a toolchain that other projects can use.

## A Bit of History

Before there was ClojureWerkz, [myself](http://twitter.com/michaelklishin) and [Alex](http://twitter.com/ifesdjeen) were fairly active in the
open source community. I maintain several RabbitMQ clients and
needed a new documentation site for [one of them](http://rubyamqp.info).

So I put together a doc site based on Jekyll and Alex helped me with styles.
This toolchain has evolved a bit and when we were looking at
writing documentation for [Monger](http://clojuremongodb.info) and [Langohr](http://clojurerabbitmq.info) in late 2011, we decided to just base them on what we already had and knew:
that Jekyll site amqp gem was using.

ClojureWerkz grew and we kept reusing the same thing over and over again.
By June 2013, ClojureWerkz has accumulated about a dozen of projects that have
substantial documentation guides. Writing, editing and maintaining these docs
took time and in the process, we've found ourselves repeating a lot of things
between sites.

It's easy to notice a lot of similarities between, say, [Elastisch docs](http://clojureelasticsearch.info) and [Langohr docs](http://clojurerabbitmq.info). We also try to take
good ideas from doc sites developed later and feed them back into older
sites.

So we needed a standard toolchain that all these documentation
projects could use. In particular, we wanted it to give us a very fast
way of writing the first couple of guides before we would worry about
finer details and editing.


## Enter ClojureWerkz Docslate

[Docslate](http://github.com/clojurewerkz/docslate) is a relatively unknown project. We don't write about it
on this blog. It does not get updates very often. It does, however,
play a major role in ClojureWerkz: powering
our documentation guides and making writing them a more pleasant
and straightforward process.


## What Is Docslate

Docslate is a Jekyll site with predefined structure and integrated Twitter Bootstrap.
Once you have it going, with just a few edits you are ready for the work that
really matters: writing helpful documentation guides.


## Why You Should Adopt For Your Project

Docslate lets you get to writing quickly without spending too much time on issues such as

 * Should I use Jekyll, Awestruct, hack my own thing with Pandoc or use a wiki?
 * What library should I use for code highlighting?
 * How do I make the docs look decent?
 * What should I license the site and content?

and so on.

It's dead easy to put together a pretty good documentation site with Docslate
and then work on copy and styling once your first version is ready to go live.


## How To Get Started With Docslate

Since Docslate uses Jekyll, you'll need Ruby (any version, although we typically
use 2.0 or 1.9.3 these days) and [RubyGems](http://rubygems.org) installed.

Then install [Bundler](http://gembundler.com/) with

    gem install bundler

Clone Doclsate Git repository with

    git clone git://github.com/clojurewerkz/docslate.git my-project-guides

Change to your local clone, remove `.git` directory and re-init the repo
(Docslate is simply a starting point, your doc site should really be in a new
repo):

    cd my-project-guides
    rm -rf ./.git
    git init
    git add .
    git commit -m "Initial commit: Docslate"

Then install dependencies with Bundler:

    bundle install --binstubs

and you are ready to run a development server with

    ./bin/jekyll serve --watch

then navigate to [localhost:4000](http://localhost:4000).

The site you'll see is very similar in structure and styles to [Elastisch docs](http://clojureelasticsearch.info), [Monger docs](http://clojuremongodb.info),
and so on.


## How To Add Content

Docslate assumes your documentation guides have an index page, a ToC page and one or more guides.
The index page is in HTML and can be found in `index.html` in the repository root.

The ToC page is in Markdown and can be found with individual guides under `articles`.

Docslate contains 3 pages for you to start with:

      guides.md
      getting_started.md
      community.md

`guides.md` is the ToC page. `getting_started.md` contains the Getting Started guide.
Finally, `community.md` gives you a page to list information about the project,
its mailing list, IRC channel, Twitter account, and other things you need to
[make your open source project really awesome](/blog/2013/04/20/how-to-make-your-open-source-project-really-awesome/).

Adding new guides is as straightforward as adding a Markdown file to the `articles` directory
with the header (title, etc) Jekyll expects and linking to it from the ToC page.

For example, to add a guide on extending your library, create a new file at `articles/extensions.md`,
add Jekyll header to it, make sure development server is started and navigate to
[localhost:4000/articles/extensions.html](http://localhost:4000/articles/extensions.html).


## How To Customize Layout

Layout files can be found under `_layouts`. There are two layouts available:

 * Default layout
 * Article layout

Article layout is used to display individual articles (guides), default layout is used for
everything else.


## How To Customize Styles and Assets

Styleshsets and JavaScript files can be found under `assets/stylesheets` and
`assets/javascripts`, respectively.


## How To Generate The Site

Use

    ./bin/jekyll build

to generate the site for deployment. Site root then will be under `_site`. This directory
is what you will deploy. It only contains static assets so deployment usually is
as straightforward as `rsync`-ing files to your server and serving them with Nginx, Apache
or any other Web server of your choice.


## Where To Go From Here

Docslate is a starting point. It is meant to be customized for your project's needs,
styling and so on. Feel free to do it, add JavaScript libraries you need, upgrade
and customize Twitter Bootstrap, and so on.


## Wrapping Up

Docslate was born out of a dozen documentation sites we have for ClojureWerkz projects.
It's a battle tested, easy to use toolchain that provides you a good starting point
and is completely open sourced under a reasonable license.

Now you don't have an excuse to not document your open source project
well!


[Michael](http://twitter.com/michaelklishin) on behalf of the [ClojureWerkz](http://clojurewerkz.org) Team.
