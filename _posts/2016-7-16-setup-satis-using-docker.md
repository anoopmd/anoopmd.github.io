---
layout: post
title: Setup Satis using Docker
---

In this post we will Set up Satis using Docker.

Clone the Repo
`git@github.com:anoopmd/docker-satis.git`

The Dockerfile in the repo that you just cloned does the following tasks.
1. Set up Ubuntu 14.04
2. Set up Nginx
3. Set up Satis
4. Set up a Cron Job to Build Satis periodically
5. Set up Http Basic Auth for accessing the Nginx
 