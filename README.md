# Nodejs Containeraisation (Docker)
[![Builds](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

---
# Description

Creating a simple Nodejsapp with help of Dockerfile to print the "Hello World".

---

# Features

- Simple nodejs Dockerfile for image creation.
- Usage of Alpine OS as base image to reduce the size of image that built.

---
# Prerequisites

- Need to have Docker installed in your machine.
- Need to have Git installed in your machine.

---
# Installation 

- [Docker installation](https://docs.docker.com/engine/install/ubuntu/) 
- Alternatively from the above, you can use Pre-installed [Docker Terminal](https://labs.play-with-docker.com/) (For the easy access to configured Docker environment especially for begineers)
- [Git installation](https://git-scm.com/download/linux)

---
# How to build a image with Dockerfile
_Steps:_
```sh
yum install docker -y
yum install git -y
git clone https://github.com/amalbosemathew/simple_nodejsapp
cd simple_nodejsapp/
docker build -t <your_image_name:tag> . 
#eg: docker build -t nodejs:1.0 .
docker image ls <------------------ image will list here
```

### Screenshots

_Downloading the docker file from Git and build a image_ 
![alt text](https://i.ibb.co/RTVG9WY/screen2.png)

---
# How to build a Container from the image

_Steps_

```sh
docker container run --name nodejs -p 3000:3000 -d nodejs:1.0
docker container ls  <--------- container listing with status
Argument explanation:
--name <----- Using for container name otherwise docker select a random name
-p     <----- Using port publish like our local port assign for that container it means localport forwards to docker container
-d     <----- Detach the container otherwise its try to enter the container
```
### Screenshots 

_Building a container from Image pulled from [Docker Hub](https://hub.docker.com/repository/docker/amalbosemathew/nodejs)

![alt text](https://i.ibb.co/S6CySDy/screen1.png)

_Container running on port 3000 and output_

![alt text](https://i.ibb.co/gMP2MCL/screen4.png)


# Additional Informations_

---
## _Push Image to Docker Hub (upload docker image to registry)_
We can upload theDocker image to [Docker hub]("https://hub.docker.com/").
### _Steps_
1. _How to login Docker hub_
```sh
docker login <----------- login with your credentials which you use in docker hub
```
2. _Docker Tag and Push_
> _Docker push is working with your docker hub username so you need to change the image name with your username_

```sh
docker tag nodejs:1.0 amalbosemathew/nodejs:1.0
docker tag nodejs:1.0 amalbosemathew/nodejs:latest
docker image push amalbosemathew/nodejs:latest
```
## _How to pull this image from Docker hub(Download image from registry)_
_Download image from Docker hub and it no needs to login docker hub._
```sh
docker image pull <your_username>/<image_name>:tag
docker image pull amalbosemathew/nodejs:latest
```
# Docker File Explanation
```sh
FROM alpine:3.8               <-------- Base Image
RUN mkdir /var/node/          <-------- RUN is using for exicute shell command
WORKDIR /var/node/            <-------- Image working directory
COPY ./app.js ./              <-------- Copy node file to WD
RUN apk update
RUN apk add nodejs npm        <-------- nodejs and npm installtion
RUN npm init -y
RUN npm install express       <-------- nodejs module installtion 
EXPOSE 3000                   <-------- Just expose which port we use in container
ENTRYPOINT [ "node" ]         <--------- EntryPoint we using our image default command and if you need to change container runing time you can use "docker run --entrypoint sh <image>:tag" when you enter this your image default command is shell 
CMD [ "app.js" ]              <--------- CMD is working the same image default command but when you use ENTRYPOINT at that time this following entry point and it works as a argument of ENTRYPOINT eg: "node app.js"
```
---
# Conclusion

The Intention of this Reposistory is to create awareness about the Dockerfile and the usage of containerisation.

<p align="center">
<a href="mailto:mathew.amalbose@gmail.com"><img src="https://img.shields.io/badge/-mathew.amalbose@gmail.com-D14836?style=flat&logo=Gmail&logoColor=white"/></a>
<a href="https://www.linkedin.com/in/amal-bose-mathew"><img src="https://img.shields.io/badge/-Linkedin-blue"/></a>
<a href="https://techbit-new.blogspot.com/"><img src="https://img.shields.io/badge/-Blogger-orange"/></a>
  

