---
layout: post
title: Brunch Examples - Compiling Handlebars
---

In this post we will see how we can use brunch to compile our handlebars templates.

Here is our directory structure for this example

<pre>
app
|-templates
|  |-home.hbs
|  |-about.hbs
|  |-contact.hbs
|-index.html
|-brunch-config.js
</pre>

Our objective is to use Brunch to convert the all the templates into an AMD compliant single file so that we can load it using [Requirejs](http://requirejs.org/) like
`require ('templates/home')` , `require ('templates/about')`

Here goes our brunch-config.js
{% highlight javascript %}
exports.config = {
  files: {
    templates: {
      joinTo: 'javascripts/app.js'
    }
  }
};
{% endhighlight %}

Now run `brunch build`

This will automatically create a public folder and put your compiled templates into `public\javascripts\app.js` file.

You can load this file in your *index.html* and load your templates like `require ('templates/home')`