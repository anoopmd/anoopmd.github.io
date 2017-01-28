---
layout: post
title: Docker Images Vs Containers
---

When using docker, we start with a base image. We boot it up, do changes and the changes are saved in layers forming another image.

An instance of an image is called container.
You have an image, which is a set of layers as described above.
If you start this image, you have a running container of this image.
You can have many running containers of the same image.

## See all images
`docker images`

## See all runnning containers
`docker ps`

## See all containers
`docker ps -a`

Sources
http://paislee.io/how-to-automate-docker-deployments/
http://stackoverflow.com/questions/23735149/docker-image-vs-container
https://github.com/docker/docker/issues/928