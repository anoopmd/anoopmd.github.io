---
layout: post
title: Global beforeEach and afterEach in Mocha
---

In many cases one would want to perform a set of certain repetitive tasks for every test.
I had a requirement where I was doing some api testing, and had to reset and seed the database for every test.

One of the methods that we can achieve this is by putting the common logic that needs to be performed before and after each test into a single file. And then require it in your tests.

[SO Link](http://stackoverflow.com/questions/10561598/global-before-and-beforeeach-for-mocha)