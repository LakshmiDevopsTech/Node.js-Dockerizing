# Dockerizing a Node.js web app
## Description
The goal of this example is to show you how to get a Node.js application into a Docker container. Its a simple "hello world" application using and the container of this web app creating using a sample Dockerfile.
## Features
- Its just a small application to understand the creation of Dockerfiles for nodejs application
- This container will occupy only a small space because the OS using is Alpine.
## Pre-Requests
- Install Docker on your machine.
## Build a image from Docker file.
The availble data's in my current working directory is:
```
[root@ip-172-31-33-253 ~]# ll
-rw-r--r-- 1 root root       237 Jul 28 12:49 app.js
-rw-r--r-- 1 root root       192 Jul 28 13:15 Dockerfile
```
Build image:
```
docker build -t <imagename:tag> .
docker build -t nodejs:1 .
```
##### screenshots
![alt text](https://github.com/LakshmiDevopsTech/Node.js-Dockerizing/blob/main/nodejs-image-build.PNG)
![alt_text](https://github.com/LakshmiDevopsTech/Node.js-Dockerizing/blob/main/nodejs-image-build-2.PNG)
![alt_text](https://github.com/LakshmiDevopsTech/Node.js-Dockerizing/blob/main/nodejs-image-build-3.PNG)

## Create container using the Image
```
docker container run --name <name of conatiner> -p <sourceport:targetport> -d <imagename:tag>
docker container run --name node -p 80:8080  -d nodejs:1
```
##### Screenshots
![alt_text](https://github.com/LakshmiDevopsTech/Node.js-Dockerizing/blob/main/nodejs-container-creation.PNG)

## Output
![alt_text](https://github.com/LakshmiDevopsTech/Node.js-Dockerizing/blob/main/nodejs-output.PNG)
## Docker File Explanation
```
FROM alpine:3.8  <-------------- Base Image
RUN mkdir /var/nodejs/ <-------- RUN will execute the shell command and create this directory
WORKDIR /var/nodejs/ <---------- Work directory of Image
COPY ./app.js . <--------------- copy this file from current directory to Working directory
RUN apk update <---------------- running updations
RUN apk add npm nodejs <-------- Installation of npm and nodejs
RUN npm init -y 
RUN npm install express <------- nodejs module (express) installtion
EXPOSE 8080 <------------------- For identify the port using in container
CMD [ "node", "app.js" ] <------ Default command running in container.
```
## Conclusion
It's just a simple nodejs application for understanding how to write a Dockerfile. If anyone have any douts, please ping me.
### ⚙️ Connect with Me

<p align="center">
<a href="mailto:lakshmipriya458@gmail.com"><img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white"/></a>
<a href="https://www.linkedin.com/in/lakshmipriya-p-c-7b5a2b88/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/></a>  
