---
layout: post
title: Hooking a Chaplin View to a DOM Element
---

In this post let us see how we can hook a Chaplin View to a DOM element. 
We want to display Hello World in our div and we want to achieve this using Chaplin View.

This may seem trivial, but our focus here is on understanding the fundamentals. 
Here is the complete html file.

{% highlight html %}
<html>
<head>
<meta charset="utf-8">  
<title>Example 1</title>  
<script src="../bower_components/requirejs/require.js"></script>

<script type="text/javascript">  
  require.config({
    paths : {
      "jquery" : "../bower_components/jquery/dist/jquery.min",
      "underscore" : "../bower_components/underscore-amd/underscore-min",
      "backbone" : "../bower_components/backbone-amd/backbone-min",
      "chaplin" : "../bower_components/chaplin/chaplin"
    }
  });
</script>

<script type="text/javascript">  
require(['chaplin', 'jquery'], function(Chaplin, $) {  
  var HelloWorldView = Chaplin.View.extend({
    autoRender : true,
    getTemplateFunction  : function(){
      return function(){
        return 'Hello World'
      }
    }
  });

  var helloWorldView = new HelloWorldView({
    container  : "#page",
  });
});
</script>
</head>
<body>  
  <div id="page">
  </div>
</body> 
</html>
{% endhighlight %}

Here are the important points to note

> Making the `autoRender` attribute as true tells Chaplin that we want to render the view as soon as the view is instantiated

> In the `container` attribute, we are passing the selector to which our view will be hooked to

> The `getTemplateFunction` expects a function to be returned. The returned function will be executed and its output will be rendered inside our dom element

In the next post, we shall implement a view which will load the content from a template file.