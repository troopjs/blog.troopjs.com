---
layout: post
title: "Bundling of mu-lib/* dependencies"
excerpt: "A discussion on mu-lib/* dependencies should be bundled or not"
tags: [3.x, enhancement]
link: https://github.com/troopjs/troopjs/issues/104
author: mikaelkaron
share: true
---

From [the github issue](https://github.com/troopjs/troopjs/issues/104):

>One of the major undertakings of v3 was to externalize generic dependencies from troop like [mu-unique](https://github.com/mu-lib/mu-unique), [mu-getargs](https://github.com/mu-lib/mu-getargs), [mu-selector-set](https://github.com/mu-lib/mu-selector-set) and lately [mu-emitter](https://github.com/mu-lib/mu-emitter) (there's a bunch more available from the [mu-lib project page](https://github.com/mu-lib), take a break and go have a look).
>
>Thanks to this we've enabled applications to take advantage of a lot of the magic that underpins troop, without actually having to use troop itself. However, this has created a bit of an issue with our bundling policies. At the moment we bundle all of these `mu-*` dependencies in the final troopjs bundle, but if you are writing an application using troop _and_ one of the included `mu-*` deps you'll realize that making a final build of your own application may not be as easy as you'd think.
>
>To resolve this we're proposing to seize bundling of `mu-*` deps. The result of this would be that application developers would themselves be responsible for creating bundles for troopjs/application dependencies.

Jump straight to the [issue](https://github.com/troopjs/troopjs/issues/104) and join the discussion.