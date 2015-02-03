---
layout: post
title: "Custom Shadow Resolution proposal"
excerpt: "Shedding some light on the Custom Shadow Resolution proposal"
tags: [3.x, enhancement]
link: https://github.com/troopjs/troopjs-compose/issues/18
author: mikaelkaron
share: true
---

From [the github issue](https://github.com/troopjs/troopjs-compose/issues/18):

>We'd like to add custom shadow resolution when composing two specs with overlapping properties but different values.
>
>Imagine this composition:
>
{% highlight javascript %}
var X = Factory({
  "one": function () { ... },
},
  "one": false
});

var x = X();
x.one === false; // true
{% endhighlight %}

>This makes total sense as compositions are composed left-to-right, however if you don't explicitly understand how your composition looked (or if you compose on someone else's object) bad things will happen.
>
>Imagine the following composition:
>
{% highlight javascript %}
var X = Factory({
 "one": function () { ... }
});

var XY = Factory(X, {
 "two": function () { ... }
});
{% endhighlight %}
>
>This all makes sense and you'll end up with one well arranged composition. But what happens if the author of `X` decides to add a `two` method? Well, we're already shadowing it in `XY`, so the final composition will have `two` from `XY`. This is most likely what the application developer expected, but is it what the author of `X` expected?

Jump straight to the [issue](https://github.com/troopjs/troopjs-compose/issues/18) and join the discussion.