# Creating_First_Docker_Image
## Introduction

  Containers are amazing 🤩 and fun 🎉. Creating a container and running ⚙ your website 🌐 inside it just take few steps, But did 🤔 you know 🧠 how to create a custom container image. Creating a custom container has some more benifits over using existing one i.e you can show off 😎, you can share your project 📁 or website which does not require any extra configutation ⚙ setup. In this repo i'm going 🏃‍♂️ to talk how to create your first container image with one  of the very famous container docker 🐳.  
  
## Pre-requisists
1. Docker 🐳 basics 
2. Familarity with command 
3. Nothing Else ❌

## First Step
  
  Very first 1️⃣ step 🚶‍♀️ to create a docker image to install 🛠 docker 🐳 . Most probably you had already done 👍 this if you are reading this article, But if not checkout installation guide 📖 [Here](https://docs.docker.com/engine/install).
  
## How to create one

  For creating images docker 🐳 provides `docker build` command. The syntax of docker 🐳 command as following
  
  ```
  docker build -t image_name dir_name
  ```
  
  Let's break down this command further
  
   1. `-t` flag is used to specify name of image.
   2. `image_name` is obiously value for `-t` flag - the name you want to give to your image
   3. `dir_name` is name of directory 📁 in which docker is going to look 👀 for a file named `Dockerfile` 😯. It's our point of interest 🤔 to get to know how to creating a docker 🐳 image.
   
## What is Dockerfile 🤔

  Docker reads instructions from Dockerfile to create an image. Basically Dockerfile specifies the step 🚶‍♂️ to take to create ⚒ a image according to your need.
  if you need more than one 1️⃣ file 📄 for distict cases then use format `<word_of_choice>.Dockerfile`.
 
## Dockerfile basic structure
 
 ```Dockerfile
 FROM <base_image>
 ADD <src> <dest>
 COPY <src> <dest>
 EXPOSE <port>
 ENTRYPOINT <cmd>
 CMD <cmd>
 ```
 
 Let's take a look 👀 at these commands
 1. `FROM` - It specifies the base image to be used. It forms base for our image. Our customization 🔧 will be placed on the top of this image. Base image can one the images available on dockerhub 🐳 which is bestfit for your usecase.
 2. `ADD` - It copies files from source in host system 💻 to the destination of image to be created.
 3. `COPY` - It also copies files from source in host system 💻 to the destination of image to be created.
 4. `EXPOSE` - This instruction is used to tell docker 🐳 to open a port inside container running this image.
 4. `ENTRYPOINT` - This specify command to be run ⚙, when image is used to run ⚙ a container.
 5. `CMD` - This is also specifies command to run every time container run ⚙. `CMD` can be overriden when running image.
 
   ```
   Note: Final command to be run determined by ENTRYPOINT + CMD
   ```
 All of the mentioned instructions for the Dockerfile is not mendatory. The use of these depends on the use cases. For references to available command visit [Here](https://docs.docker.com/engine/reference/builder/)
 
## Build image
    
   
 
