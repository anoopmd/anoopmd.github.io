---
layout: post
title: Implementing Modals in Chaplin JS
---

Modals are one of the common things that you will come across while developing most applications.
In this post we will cover the implementation of modal views in Chaplin JS.<br>

This post assumes that you know the basics of ChaplinJS and Brunch and have expeimented some examples with them.

We will be using the following libraries in this example used<br>
```
ChaplinJS, Bootstrap, Handlebars, Jquery
```

The directory structure is given below.

<pre>
app
|-assets
|  |--index.html
|--templates
|  |-modal.hbs
|--views
|  |-modal.js
|-bower.json
|-config.json
|-brunch-config.js
</pre>

Here is our Modal Template
{% highlight html %}
{% raw %}
<div class="modal-dialog">
  <div class="modal-content">
    <div class="modal-header">
      <button type="button" class="close" data-dismiss="modal" aria-hidden="true"> x </button>
      <h4 class="modal-title">{{{title}}}</h4>
    </div>
    <div class="modal-body">
      {{{content}}}
    </div>
    <div class="modal-footer">
      <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
    </div>
  </div>
</div>
{% endraw %}
{% endhighlight %}

Here is our Modal View

{% highlight javascript %}
'use strict';

var template = require('templates/modal');

module.exports = Chaplin.View.extend({
  optionNames: Chaplin.View.prototype.optionNames.concat(['template', 'title', 'content']),
  autoRender : true,
  template : template,
  getTemplateFunction : function(){
    return this.template;
  },
  getTemplateData : function(){
    return {
      title : this.title,
      content : this.content
    }
  },
  show: function() {
    var self = this;

    this.$modal = $('#' + this.id);
    this.$modal.modal();

    this.$modal.on('hidden.bs.modal', function () {
      self.hide();
    });
  },
  hide: function() {
    this.$modal.modal('hide').remove();
  }
});
{% endhighlight %}

And here is our html.
{% highlight html %}
<html>
  <head>
  <meta charset="utf-8">
    <link href="/stylesheets/vendor.css" rel = "stylesheet"/>
    <script src="/javascripts/app.js"></script>
    <script src="/javascripts/vendor.js"></script>
  </head>
  <body>
  </body>
  <script>
    var ModalView = require('views/modal');
    var modalView = new ModalView({
      id : 'alert-model',
      container : 'body',
      className : 'modal fade alert-modal',
      title : 'Hello World',
      content : 'Its Awesome !!!'
    });
    modalView.show();
  </script> 
</html>
{% endhighlight %}

Lets finally add our brunch-config.js
{% highlight javascript %}
exports.config = {
  files: {
    javascripts: {
      joinTo: {
        'javascripts/app.js': /^app/,
        'javascripts/vendor.js': /^(?!app)/
      }
    },
    templates: {
      joinTo: 'javascripts/app.js',
    },
    stylesheets: {
      joinTo : 'stylesheets/vendor.css'
    }
  }
};
{% endhighlight %}

Now run the following command in your terminal

```
brunch watch --server
```

This should automatically build your app, and you can open `localhost:3333` in your browser to view the example in action.

The source code of this example can be found [here](https://github.com/anoopmd/chaplinjs-examples/tree/master/implementing-modals)