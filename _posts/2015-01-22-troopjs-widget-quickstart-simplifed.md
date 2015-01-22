---
layout: post
title: TroopJS widget quickstart simplified
author: mikaelkaron
excerpt: "The TroopJS widget quickstart just got even quicker"
tags: [3.x]
---

We just released an even simpler [troopjs widget quickstart](https://github.com/troopjs/troopjs-widget-quickstart/) for you all to enjoy. Not that it was complicated before, but now this is all you have to is to pick any of the two examples from below and get going!

## Separated

This will keep your initial HTML and JS separated. Start with `index.html`

{% highlight html %}
<!DOCTYPE html>
<html>
<head lang="en">
  <meta charset="UTF-8">
  <title>Your Project</title>
</head>
<body>
  <span data-weave="your-project/widget">wait for it...</span>
  <script src="bower_components/requirejs/require.js" data-main="index.js"></script>
</body>
</html>
{% endhighlight %}

Then continue with `index.js`

{% highlight js %}
require.config({
  "baseUrl": "bower_components",
  "packages": [{
    "name": "jquery",
    "location": "jquery/dist",
    "main": "jquery.min"
  }, {
    "name": "your-project",
    "location": ".."
  }],

  "deps": [ "jquery", "require", "troopjs/main", "troopjs-widget/main" ],

  "callback": function (jQuery, localRequire) {
    localRequire([ "troopjs-widget/application" ], function (Application) {
      jQuery(function ($) {
        Application($("html"), "application").start();
      });
    });
  }
});
{% endhighlight %}

## Combined

If for some reason you want this all in one file just make this your `index.html`:

{% highlight html %}
<!DOCTYPE html>
<html>
<head lang="en">
  <meta charset="UTF-8">
  <title>Your Project</title>
  <script>
  var require = {
    "baseUrl": "bower_components",
    "packages": [{
      "name": "jquery",
      "location": "jquery/dist",
      "main": "jquery.min"
    }, {
      "name": "your-project",
      "location": ".."
    }],

    "deps": [ "jquery", "require", "troopjs/main", "troopjs-widget/main" ],

    "callback": function (jQuery, localRequire) {
      localRequire([ "troopjs-widget/application" ], function (Application) {
        jQuery(function ($) {
          Application($("html"), "application").start();
        });
      });
    }
  };
  </script>
</head>
<body>
  <span data-weave="your-project/widget">wait for it...</span>
  <script src="bower_components/requirejs/require.js"></script>
</body>
</html>
{% endhighlight %}