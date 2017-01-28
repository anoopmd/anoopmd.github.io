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
`composer create-project composer/satis=1.0.0-alpha2 --stability=dev --keep-vcs`

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
  	"laravel/lumen" : "*"
  }
}
{% endhighlight %}

## Build Satis<br>
`php bin/satis build satis.json html/`

You might be asked to generate a token, in which case you will be given a link to generate a token.
This will be stored in /.composer/auth.json for future use by Composer.

Now Open 127.0.0.1 in your browser

If everything went well, you must see the page similar to the below one

<img src="{{ site.baseurl }}/images/Satis.png" style="width: 400px;"/>

### Setting up a Cron Job
Lets schedule a Cron Job that Builds Satis at specific intervals

`crontab -e`

Add the below line to schedule the Satis Build for every 5 min.

`*/5 * * * * php /usr/share/nginx/satis/bin/satis build /usr/share/nginx/satis.json /usr/share/nginx/html/`

Restart your Cron Task <br>
`sudo /etc/init.d/cron restart`

Now Satis Build would be automated !!

