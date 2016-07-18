---
layout: post
title: Cron Job Notes
---

<pre>
*     *     *   *    *        command to be executed
-     -     -   -    -
|     |     |   |    |
|     |     |   |    +----- day of week (0 - 6) (Sunday=0)
|     |     |   +------- month (1 - 12)
|     |     +--------- day of        month (1 - 31)
|     +----------- hour (0 - 23)
+------------- min (0 - 59)
</pre>

### Examples
<pre>
30     18         *        *     * each day at 6:30 PM
30      0         1   1,6,12     * On Each at 1st of Jan, Jun & Dec at 00:30
0      20         *       10   1-5 On Mon, Tue, Wed, Thu, Fri Every Week of Oct at 20:00
0       0   1,10,15        *     * 1st, 10th and 15th of every month at 00:00
5,10    0        10        *     1 Every Monday and 10th of Every Month at 00:05 and 00:10
</pre>

### Creating a Cron Job
sudo crontab -e 
sudo VISUAL=vim crontab -e (To open in Vim) 
Save your Cron Jobs here
Ex : * * * * * COMMAND

### Online Testing
[Cron WTF] (http://cronwtf.github.io/)

### Reference
[Cron Tab Quick Reference](http://www.adminschoice.com/crontab-quick-reference) <br>
[Ubuntu 14.04](https://vexxhost.com/resources/tutorials/how-to-use-cron-jobs-for-automation-on-ubuntu-14-04/) <br>
[Short Introduction](https://www.howtoforge.com/a-short-introduction-to-cron-jobs) <br>