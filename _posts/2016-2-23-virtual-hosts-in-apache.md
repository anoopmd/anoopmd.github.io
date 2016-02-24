---
layout: post
title: Virtual Hosts in Apache
---

In this post we will look at how we can configure a virtual host in Apache 2.4.
I am assuming you are using Windows OS

###Installing Apache 2.4
You should already have Apache setup manually. If you havent done it, here are the steps.

a. Download the apache binaries from [Apache Lounge](https://www.apachelounge.com/download/)

b. Unzip it and place the Apache24 directory in your C drive
  <pre>
  C:
  |-Apache24
  |  |-bin
  |  |-cgi-bin
  |  :
  |  :
  |
  |-REEADME.txt
  </pre>

c. In case you get the `Unable to start the program as VCRUNTIME140.dll is missing on your computer.` ERROR you can download and install the C++ Redistributable for Visual Studio 2015 RC from [here](http://www.microsoft.com/en-us/download/details.aspx?id=48145)

d. Now navigate to the `bin` folder under `Apache24` and run/execute `httpd.exe`

e. Open your browser and load 127.0.0.1. If all went well you shouls see `It Works` in your screen.

###Configuring a Virtual Host

Open the config file located at `Apache24/conf/httpd.conf`

Add the below lines at the end of the file
{% highlight html %}

<VirtualHost *:80>
    # This first-listed virtual host is also the default for *:80
    ServerName www.helloworld.com
    ServerAlias helloworld.com 
    DocumentRoot "c:/Apache24/htdocs/helloworld"
</VirtualHost>

{% endhighlight %}

> The document root will specify the path from where your files will be loaded to the server

###Configuring hosts file
Open the hosts file located at `C:\Windows\System32\drivers\etc\hosts`

Add the below entry
{% highlight html %}
127.0.0.1   www.helloworld.com
{% endhighlight %}

> Now, When you load `www.helloworld.com` in your browser, it will load it from your local apache server.


If all went well, When you load `www.helloworld.com` in your browser, it should load the files from your `c:/Apache24/htdocs/helloworld` directory which you had mentioned as the DocumentRoot in the VirtualHost settings in your `httpd.conf` file.