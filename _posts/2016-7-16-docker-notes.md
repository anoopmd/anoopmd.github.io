---
layout: post
title: Docker Notes
---

Installation
For Details Refer : [Official Doc](https://docs.docker.com/engine/installation/linux/ubuntulinux/)
1. sudo apt-get install apt-transport-https ca-certificates
2. sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
3. Open /etc/apt/sources.list.d/docker.list
   Add deb https://apt.dockerproject.org/repo ubuntu-trusty main
   (This is for Ubuntu Trusty 14.04 (LTS))
4. sudo apt-get update
5. sudo apt-get install docker-engine
6. sudo service docker start
7. Test By Running sudo docker run hello-world

List All Containers in The system
sudo docker ps -a

Show Running Containers
docker ps

Last Container Started
docker ps -l

List Docker Images
sudo docker images

Starting a Docker Container
docker start nostalgic_morse

Removing a Docker Container
docker rm nostalgic_morse

Stopping a Docker Container
sudo docker stop pensive_saha

Building Your Docker Image
1. mkdir mydockerbuild
2. cd mydockerbuild
3. touch Dockerfile
4. vim Dockerfile
   FROM docker/whalesay:latest
	 RUN apt-get -y update && apt-get install -y fortunes
	 CMD /usr/games/fortune -a | cowsay
5. docker build -t docker-whale .
6. docker run docker-whale

Running a web application in Docker
1. docker run -d -P training/webapp python app.py
2. docker run -d -p 80:5000 training/webapp python app.py
   (This would map port 5000 inside our container to port 80 on our local host)
   You should See Hello World

Installing Docker Compose
1. sudo apt-get install python-pip
2. sudo pip install docker-compose
