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

   Ubuntu 16
   Add "deb https://apt.dockerproject.org/repo ubuntu-xenial main"

4. Update the package database with the Docker packages from the newly added repo:
   sudo apt-get update

5. Make sure you are about to install from the Docker repo instead of the default Ubuntu 16.04 repo:
   apt-cache policy docker-engine

6. sudo apt-get install docker-engine
7. sudo service docker start

8. Docker should now be installed, the daemon started, and the process enabled to start on boot.
   Check that it's running:
   `sudo systemctl status dockerproject`

9. Test By Running sudo docker run hello-world

## List All Containers in The system
`sudo docker ps -a`

## Show Running Containers
`docker ps`

## Last Container Started
`docker ps -l`

## List Docker Images
`sudo docker images`

## Starting a Docker Container
`docker start nostalgic_morse`

## Removing a Docker Container
`docker rm nostalgic_morse`

## Stopping a Docker Container
`sudo docker stop pensive_saha`

## Building Your Docker Image
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

## Installing Docker Compose
1. sudo apt-get install python-pip
2. sudo pip install docker-compose

## Delete All Images
`sudo docker rmi -f $(sudo docker images -q)`

## Delete All Containers
`sudo docker rm $(sudo docker ps -a -q)`

## See docker logs of a container
`sudo docker logs <CONTAINER_ID>`

## Bash into a running container
```bash
$ sudo docker exec -i -t 665b4a1e17b6 /bin/bash #by ID
or
$ sudo docker exec -i -t loving_heisenberg /bin/bash #by Name
$ root@665b4a1e17b6:/#
```


## Installing Docker Compose
sudo apt-get install python-pip
sudo pip install docker-compose