---
layout: post
title: "Service Locator Proposal"
excerpt: "Extracting the `locator` part from the Service Proxy Proposal"
tags: [3.x, enhancement]
link: https://github.com/troopjs/troopjs/issues/95
author: mikaelkaron
share: true
---

From [the github issue](https://github.com/troopjs/troopjs/issues/95):

> While developing the service locator code for [troopjs/troopjs#93](https://github.com/troopjs/troopjs/issues/93) we started asking ourselves some important questions, amongst them:
>
> > Are TroopJS services:tm: the only type of component tha can be shared in an application?
>
> and
>
> > Could there be more ways of grouping components than global and local?
>
> Half of one nights worth of sleep and a few cups of coffee later the answers are:
>
>  1. _Probably not_
>  1. _Probably more_
>
> This indicated to us that the original goal of just implementing service proxies was overshadowed by an even more important proposal for something like a service locator (we're using the word service loosely here). And thus this proposal was initiated.

Jump straight to the [issue](https://github.com/troopjs/troopjs/issues/95) and join the discussion.