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

  Dockerfile specifies the step 🚶‍♂️ to take to create ⚒ a image according to your need.  
  
