---
layout: post
title: Setting Up Satis Locally on Nginx
---

I am using Ubuntu 14.04. The default public directory is /usr/share/nginx/html

### Pre-requisites
* Nginx
* Composer
* Php

Navigate to the below dir<br>
`cd /usr/share/nginx`

Install Satis via Composer<br>
`composer create-project composer/satis --stability=dev --keep-vcs`

Configure Satis<br>
/usr/share/nginx/satis.json
{% highlight javascript %}
{
  "name": "Acme Company",
  "homepage": "http://packages.acme.company",
  "repositories": [
    {
      "type": "git",
      "url": "git@github.com:laravel/lumen.git"
    }
  ],
  "require": {
  	"laravel/lumen" : "2.3.*"
  }
}
{% endhighlight %}

## Build Satis<br>
`php bin/satis build satis.json html/`

Now Open 127.0.0.1 in your browser

If everything went well, you must see the page similar to the below one

<img src="{{ site.baseurl }}/images/Satis.png" style="width: 400px;"/>