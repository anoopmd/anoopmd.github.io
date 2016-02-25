---
layout: post
title: Configuring PHP with Apache
---

In this post we will look at how we can configure a PHP 5.x to be used by Apache 2.4
I am assuming you are using Windows OS

If you havent installed Apache , you can refer [this](http://anoopmd.github.io/virtual-hosts-in-apache/) post for the steps to install it.

### Installing PHP
If you havent installed PHP, here are the steps.

a. Download the PHP binaries from [here](http://windows.php.net/download/)

b. Unzip it and place the contents in `C:/Php`
  <pre>
  C:
  |-Php
  |  |-dev
  |  |-ext
  |  :
  |  :
  |
  |-readme-redist-bins.txt
  </pre>

c. Now navigate to the `C:/Php` folder run/execute `php --version`

d. If all went well you should see the version details

### Configuring Php to be used by Apache 2.4

Open the config file located at `Apache24/conf/httpd.conf`

Add the below lines at the end of the file
{% highlight html %}

LoadModule php5_module "C:/Php/php5apache2_4.dll"
AddHandler application/x-httpd-php .php

# configure the path to php.ini
PHPIniDir "C:/Php/php"

{% endhighlight %}

> Do not forget to restart your Apache server in order for the changes to take effect.

### Testing
Create the following file `test.php` under htdocs

Add the below entry
{% highlight php %}
<?php

echo phpinfo();
{% endhighlight %}


If all went well, When you load `127.0.0.1/test.php` in your browser, it should show you the php configuration.