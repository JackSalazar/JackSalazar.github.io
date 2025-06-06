---
title: Dockerized LAMP Stack
date: 2025-06-06
description: This will guide you in creating a LAMP Stack inside Docker from scratch.
categories: ['Tutorial']
draft: false # Change to true to not render the post in on the website
#image: " "
---


The goal provided is as follows:
Create a new machine and create a LAMP stack in a container. Any container will do, but for this documentation, docker will be used.
For this, you will need the following applications:
Docker: Container
**L**   inux: The operating system used, which in this case will be alpine
**A**  pache2: The http server to access the website in the first place
**M** ySQL: The database which has all the data of the website
**P**  HP: The scripting language

### Setting up Alpine
Step 1 is of course to set up alpine in the first place

log in as root
```
root
```
To save yourself from struggling, just follow the set up executable
```
setup-alpine
```

From here, it guides you through the whole setup process. Here's an example of the commands you should enter

```
us
us
[hostname]
eth0
dhcp
n
[yourPassword]
[yourPassword]
US/Pacific
none
chrony
https://dl-cdn.alpinelinux.org/alpine/v3.20/main
[name]
[name]
[namePassword]
[namePassword]
none
openssh
sda
sys
y
reboot
```
Note: The link for the alpine repository is subject to change. Replace v3.20 with the version that you are running. Verify that the website is working by going there on a gui 

## Installing proper Packages

First, modify /etc/apk/repositories 
```
vi /etc/apk/repositories
```
In there, add the following line
```
https://dl-cdn.alpinelinux.org/alpine/v3.20/community
```

Save, then proceed to update and upgrade the repositories

```
apk update && apk upgrade
```

From here, you can now download docker

```
apk add docker
```

## Configuring Docker

By default, the service isn't enabled nor started, so enter the following

```
rc-update add docker default
openrc --service docker start
```

Now, you could go through the pain and troubleshooting of making your own LAMP stack, or you can just take it from the dockerhub

```
docker pull fauria/lamp
```

```
docker run -itp 80:80 fauria/lamp /bin/bash
```

## Inside the Container

You'll find yourself in the docker container. 
From here, you need to start apache2

```
service apache2 start
```

From here, you can access the website from the original machine's ip
