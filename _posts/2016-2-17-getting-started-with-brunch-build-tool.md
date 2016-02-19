---
layout: post
title: Getting Started with Brunch Build Tool
---

The main intention of the post is to provide the steps so that you can have brunch set up and running in no time.

Lets start with something very simple. We want to concatenate all the javascript files within a directory. Lets see how we can do it.

You should have Node.js and npm installed in your machine.
If you haven't installed brunch, you can do this by executing the following command.

```
npm install -g brunch
```

Let us assume you have a directory structure like the one below
<pre>
app
|-js
  |-animals.js
  |-vehicles.js
</pre>
Our task is to concatenate the files under the js directory

Lets create a **brunch-config.js** file under the app folder
{% highlight javascript %}
exports.config = {
  files: {
    javascripts: {
      joinTo: {
        'javascripts/app.js': /^app/
      }
    }
  }
};
{% endhighlight %}

Lets also create a package.json file to load the dependencies required by brunch to concatenate the js file

{% highlight javascript %}
{
  "name": "simple-brunch",
  "version": "0.0.1"
}
{% endhighlight %}
Lets install the javascript-brunch plugin
```
npm install --save-dev brunch javascript-brunch
```

Now run
`brunch build`
This will automatically create a public directory and put your concatenated file under the public/javascripts folder

The source code of the following example can be found [here](https://github.com/anoopmd/brunch-js-concat-example)
