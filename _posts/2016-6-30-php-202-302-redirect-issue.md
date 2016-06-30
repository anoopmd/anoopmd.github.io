---
layout: post
title: PHP 202 302 Redirect Issue
---

I have spent more than a day because of this issue.
Setting the Location header will set a status code of 202 to 302.

I've gone through the following threads

[PHP Bug on 202-302 Redirect](https://bugs.php.net/bug.php?id=70273)

[PHP Bug on header("Location:") changing HTTP status](https://bugs.php.net/bug.php?id=51749)

[Stack Overflow Discussion](http://stackoverflow.com/questions/26199228/is-the-use-of-location-header-in-http-202-response-rfc-compliant)

In my opinion, PHP should not change the status code if it has been forecfully set before.

The following code overrides the previously set status code
{% highlight php %}
header("HTTP/1.1 503 Service Unavailable", true, 503);
header("Location: http://www.php.net/");
{% endhighlight %}

[RFC 7231](https://tools.ietf.org/html/rfc7231#section-6.3.3) makes no mention of the Location header while describing 202 Accepted Status code

[RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.1) mentions about sending a 202 Response with the location header which can be used to facilitate the operation of asynchronous requests.

[RFC 3875](https://tools.ietf.org/html/rfc3875#section-6.2.3) says that if the script returns an absolute URI path in a Location header field together with an attached document. The Status header field MUST be supplied and MUST contain a status value of 302 'Found', or it MAY contain an extension-code, that is, another valid status code that means client redirection.

All the above being said. I kind of side with a comment in [this](https://bugs.php.net/bug.php?id=70273) thread 
To quote it 
{% highlight php %}
Further - the REST specification has chosen to set the status 202+Location under some circumstances. That is perfectly valid with the HTTP specification too, because the Location header is not bound to any specific status.

However where your position is not valid - the PHP implementation is a generic one, it is not dedicated specifically to REST, AJAX, anything else. But, the PHP implementation makes possible to implement whatever a programmer needs. It were valid if you were filing a ticket about a REST specific implementation, maybe. Or if there were no possibility to override the status. Given this and also with the regard to the backward compatibility it doesn't look like a bug. There are many REST frameworks which could be probably more of use for you, if you don't want to implement it yourself.
{% endhighlight %}

I do not recommend removing the Location header, But I like the idea of setting the status forecfully before you return the reponse. Something along the lines of [this](https://github.com/yiisoft/yii2/issues/9412)

Thanks for reading !!