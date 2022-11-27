# Creating_First_Docker_Image
## Introduction

  Containers are amazing 🤩 and fun 🎉. Creating a container and running ▶ your website 🌐 inside it just take few steps, But did 🤔 you know 🧠 how to create a custom container image. Creating a custom container has some more benifits over using existing one i.e you can show off 😎, you can share your project 📁 or website which does not require any extra configutation ⚙ setup. In this repo i'm going 🏃‍♂️ to talk how to create your first container image with one  of the very famous container docker 🐳.  
  
## Pre-requisists
1. Docker 🐳 basics 
2. Familarity with command 
3. Nothing Else ❌

## First Step
  
  Very first 1️⃣ step 🚶‍♀️ to create a docker 🐳 image to install 🛠 docker 🐳 . Most probably you had already done 👍 this if you are reading this article, But if not checkout installation guide 📖 [Here](https://docs.docker.com/engine/install).
  
## How to create one

 For creating images docker 🐳 provides `docker build` command. The syntax of docker 🐳 command as following
  
  ```
  docker build -t image_name dir_name
  ```
  
  Let's break down this command further
  
   1. `-t` flag is used to specify name of image.
   2. `image_name` is obiously value for `-t` flag - the name you want to give to your image
   3. `dir_name` is name of directory 📁 in which docker is going to look 👀 for a file named `Dockerfile` 🤔. It's our point of interest 🤔 to get to know how to creating a docker 🐳 image.
   
## What is Dockerfile 🤔

  Docker 🐳 reads instructions from Dockerfile to create an image. Basically Dockerfile specifies the step 🚶‍♂️ to take to create ⚒ a image according to your need.
  if you need more than one 1️⃣ file 📄 for distict cases then use format `<word_of_choice>.Dockerfile`.
 
## Creating Dockefile
 
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
 2. `ADD` - It copies files 🗃 from source in host system 💻 to the destination of image to be created.
 3. `COPY` - It also copies files 🗃 from source in host system 💻 to the destination of image to be created.
 4. `EXPOSE` - This instruction is used to tell docker 🐳 to open a port inside container running ▶ this image.
 4. `ENTRYPOINT` - This specify command to be run ▶, when image is used to run ▶ a container.
 5. `CMD` - This is also specifies command to run ▶ every time ⏲ container run ▶. `CMD` can be overriden when running ▶ image.
 
   ```
   Note: Final command to be run determined by ENTRYPOINT + CMD
   ```
 All of the mentioned instructions for the Dockerfile is not mendatory. The use of these depends on the use cases. For references to available command visit [Here](https://docs.docker.com/engine/reference/builder/)
 
## Let's take an Example
  ### Scaenario
   Consider we want to dockerize our `Hack The Number` static site. Which looks like something this
   
   ![Hack the number home screen](https://user-images.githubusercontent.com/61611561/202146123-80da9007-d472-48ce-ad0c-de3eab997eab.png)
   
   ### Create a directory
    
    For the project create a new directory with the following command and move to it 
    ```
    mkdir hackdir
    cd hackdir
    ```
    
  ### Create Dockerfile
  
   1. Create Dockerfile in directory
  
       ```
       nano Dockerfile
       ```
       
   2. Paste the following code 👩‍💻 inside file 📄
    
       ```Dockerfile
       FROM nginx
       ADD src/* /usr/share/nginx/html/
       EXPOSE 80
       CMD ["nginx","-g","daemon off;"]
       ```
      Let's break 🔨 docker the following commands
        1. `FROM nginx` - This line tells docker 🐳 to use Nginx 🆖 as the official image as a base image for our new image.
        2. `ADD src/* /usr/share/nginx/html/` - This line copies files 🗃 of `src` folder inside the `/usr/share/nginx/html/` folder of image. `/usr/share/nginx/html/` folder is used by the nginx 🆖 server as entry point of website.
        3. ```EXPOSE 80``` - This line tells docker 🐳 to open port 80 inside the docker 🐳 container so that we can communicate with the nginx 🆖 server inside.
        4. ```CMD ["nginx","-g","daemon off;"]``` - This last cline starts Nginx 🆖 server and runs ▶ every time the docker 🐳 container start.
       
   3. Download the src folder 📂 from this repo to your directory 📁
   4. Now your hackdir will look 👀 like following
      
      ```
      hackdir/
         Dockerfile
         src/
            index.html
      ```
      
   6. Now run ▶ the following command
   
      ```
      docker build -t hackthenumber .
      ```
      
   5. To test your image run ▶ the following commands
   
      ```
      docker run -dp 80:80 hackthenumber
      ```
      
   6. Now visit the localhost. If everything done correctly you will see following output 
   
      ![Hack the number home screen](https://user-images.githubusercontent.com/61611561/202146123-80da9007-d472-48ce-ad0c-de3eab997eab.png)
      
## Conclusion 
   1. Building a container image can feel a litle bit anoying at very first 0️⃣ but after understanding some basic it will be piece of cake 
   2. It involve Three 3️⃣ step
      1. Create your application
      2. Create Dockerfile according to your need
      3. Run ▶ the docker build command

## Quick tools
 
 1. If you don't have docker 🐳 installed ⚙ or don't want to do, then try it from [Here](https://labs.play-with-docker.com/). Just login with dockerhub credentials and you are good to go.
 2. Try outout `Hack The Number` game from here 👉 [Hack The Number](src/index.html).
 3. Got stuck at syntax errors? Try some Dockerfile validator like [FROM latest](https://www.fromlatest.io/)
     


