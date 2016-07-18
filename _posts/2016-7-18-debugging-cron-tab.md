---
layout: post
title: Debugging Cron Tab Issues
---

Yesterday, I was learning to set up Satis on my local. That went well.
The next task was to set up a cron job that builds every 5 min.
That part sucked :(
For some reason the Cron Job would never run.
I guess I was mentally depleted by the time I got Satis up and running.

Today, I am going to debug the Cron Issue.
OK. For Some reason, Its working now. Yesterday, I was trying to edit sudo crontab -e
Today, I just tried with plain crontab -e (Without the sudo part)

Now since this is working, I tried to get the Satis build command working as a normal user.
For this, I had to adjust the permissions of ertain directories such as /usr/share/nginx/html

Once I achieved this using the following command <br>
`php /usr/share/nginx/satis/bin/satis build /usr/share/nginx/satis.json /usr/share/nginx/html/`

I updated the command in crontab -e.

And it works now !!
Satis build is now automated !!

As many would agree, when nothing seems to work and you are unable to troubleshoot the issue,
It is always better to come back later and look at it.

