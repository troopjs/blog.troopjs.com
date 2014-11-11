---
layout: post
title: Working towards 3.0.0-rc.1
author: mikaelkaron
excerpt: "A brief state of the union as we work ourselves towards a 3.0.0-rc.1 release"
tags: [3.x, releases]
---

## State of the union

Over the last few months we've been working hard on the upcoming [3.0.0](https://github.com/troopjs/troopjs/milestones/3.0.0) release. The last release was [3.0.0-pr.2+fa7fcdb](https://github.com/troopjs/troopjs/releases/tag/3.0.0-pr.2%2Bfa7fcdb) which was published June 10th.

Since then a lot of things have been done and we'll be publishing a series of blog posts here explaining the (major) changes done in 3.x but before that I'd like to take some time to outline the current plan of attack and the dates and milestones we are aiming for.

### 2014-11-11 : 3.0.0-pr.3

It's essential that developers can get their hands on the latest and greatest ASAP, so we've decided to push another PR release out there for you to play with. This release will include:

#### Framework, Stack and Contrib

To keep the learning curve for a new(ish) framework low you have to limit what a developer _has_ to know in order to get started.

Previous versions of TroopJS has been focused on adding features (1.x) and refining work-flows and adding components (2.x) and this has resulted in quite a bit of code laying around that developers _could_ use, but rarely do. It's not that the code was bad or not generic enough, it's just that for a lot of projects it simply did not fit any use cases.

This created confusion (what does this component do, should I use it?) and increased the perceived difficulty of adopting TroopJS. In 3.x we intend to get back on track and have to address this split what used to be called "the Framework bundle" into two separate parts of the TroopJS distribution.

##### Framework

This is the hyper-generic part of TroopJS that is the foundation for everything TroopJS. We've cut this down to these packages:

- [troopjs-compose](https://github.com/troopjs/troopjs-compose) : Object composition
- [troopjs-log](https://github.com/troopjs/troopjs-log) : Logging
- [troopjs-core](https://github.com/troopjs/troopjs-core) : Base components
- [troopjs-dom](https://github.com/troopjs/troopjs-dom) : DOM components

That's it. No more [troopjs-jquery](https://github.com/troopjs-archive/troopjs-jquery), [troopjs-requirejs](https://github.com/troopjs-archive/troopjs-util) and [troopjs-util](https://github.com/troopjs-archive/troopjs-util) packages. So where did all of that code go? Well, most of that code was even more generic than TroopJS itself (!) so we decided to create a new project called [mu-lib](https://github.com/mu-lib/) where most of the individual utilities and plugins can be found (and lots more with them).

##### Stack

Here we've collected officially supported extensions to the framework. These packages (will) always work with the latest version of TroopJS and will receive the same level of support as framework packages.

- [troopjs-route](https://github.com/troopjs/troopjs-route/) : Routing
- [troopjs-route-hash](https://github.com/troopjs/troopjs-route-hash): Hash based routing
- [troopjs-pubsub](https://github.com/troopjs/troopjs-pubsub) : PubSub proxying between contexts
- [troopjs-ajax](https://github.com/troopjs/troopjs-ajax) : Simple Ajax
- [troopjs-widget](https://github.com/troopjs/troopjs-widget/) : Weavable widgets
- [troopjs-compat](https://github.com/troopjs/troopjs-compat/) : Compatibility layer for apps written in 2.x
- [troopjs-cordova](https://github.com/troopjs/troopjs-cordova/): Cordova extensions for TroopJS

This is not a complete list (basically there's more to come) but this should give you an idea of what's going on.

##### Contrib

The best frameworks come pre-assembled, ours does to but we wanted a space dedicated to full-stack components so we created the [troopjs-contrib](https://github.com/troopjs-contrib) project packed with ready to use components. These components are intended to be highly reusable and _should_ work with the latest version of TroopJS (but effort is first spent on stack, then on contrib). Some examples of contrib components are:

- [troopjs-contrib-bootstrap](https://github.com/troopjs-contrib/troopjs-contrib-bootstrap/) : Bootstrap 3 extensions
- [troopjs-contrib-audio5js](https://github.com/troopjs-contrib/troopjs-contrib-audio5js/) : Wrapper around the excellent [audio5js](https://github.com/zohararad/audio5js) library
- [troopjs-contrib-audio5js-player](https://github.com/troopjs-contrib/troopjs-contrib-audio5js-player/) : Audio player with UI integration
- [troopjs-contrib-form](https://github.com/troopjs-contrib/troopjs-contrib-form/) : Form utilities and validators
- [troopjs-contrib-com](https://github.com/troopjs-contrib/troopjs-contrib-com/) : Component Object Model flow control
- [troopjs-contrib-markdown](https://github.com/troopjs-contrib/troopjs-contrib-markdown/) : Wrapper and UI components for the [markdown](https://github.com/evilstreak/markdown) library

This list will grow exponentially (well, maybe not _exponentially_, but hopefully _fast_) once we manage to kick 3.0.0 out of the door.

#### Framework re-bundle

The framework bundle has always been a bit confusing, because of the way we use(d) to tag our releases there's been a _lot_ of confusion around what builds are available and how they are packaged.With 3.x we're trying to fix this by _only_ tagging bundle builds from now on, so if you `bower install troopjs#3.0.0-pr.3` you should _only_ get the bundle and dependent 3rd party modules (like jQuery, when and poly).

However, if you `bower install troopjs#develop` the individual `troopjs-*` packages will be pulled. This should make it simpler to not only install the bundle, but also to do framework development alongside application development.

#### Better API documentation

We've worked hard on getting all of framework and stack documented. This _is_ a work in progress but all 3.x releases come with [docs](http://troopjs.com/releases/3.x/docs/). Before we release 3.0.0 we also intend to add a ton of full-application guides and feature-guides to help developers write scalable applications with TroopJS.

### 2014-11-28 : Initial release of troopjs-compat

The upgrade from 1.x to 2.x was a pain in the ass, everything changed and shit was literally all over the place. We want to - no - _need_ to avoid that this time around. To make upgrades smooth and easy we're starting working on [troopjs-compat](https://github.com/troopjs/troopjs-compat) which will act like a compatibility layer that makes 3.x look and act like 2.x. In addition to being a slot-in-compatibility-layer for existing 2.x applications troopjs-compat will also help by telling the developer what part of the application needs to change in order to be able to remove the compatibility layer entirely.

This is in no way a simple task and we'll need your help to make sure this package is air-tight and works well with existing applications. From 2014-11-17 and onwards this is where the core team will be focusing their efforts so get ready to help out.

### 2014-12-01 : 3.0.0-rc.1

If all goes well we want to have the first release candidate for 3.0.0 out in time for December 1st, and if the rc is high quality we hope to be celebrating the new year with a solid, feature complete, well documented and tight 3.0.0 release.
