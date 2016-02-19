---
layout: post
title: Brunch Examples - Compiling Sass
---


In our previous post, we learnt how to concatenate javascript using brunch.

In this post we will look at an example where we can compile our [sass](http://sass-lang.com/) files.

Let us assume you have a directory structure like the one below
<pre>
app
|-sass
  |-main.scss
</pre>

Our task is to compile our **main.scss** file.

Lets create a **brunch-config.js** file under the app folder
{% highlight javascript %}
exports.config = {
  files: {
    stylesheets: {
      joinTo: 'stylesheets/app.css'
    }
  }
};
{% endhighlight %}

Lets also create a package.json file to load the dependencies required by brunch to concatenate the js file
{% highlight javascript %}
{
  "name" : "simple-brunch",
  "version" : "0.0.1"
}
{% endhighlight %}


Lets install the sass-brunch plugin
```
npm install --save-dev brunch sass-brunch
```

Now run
```
brunch build
```
This will automatically create a public directory and put your compiled css file under the public/stylesheets folder

The source code of the following example can be found [here](https://github.com/anoopmd/brunch-examples/tree/master/brunch-sass)