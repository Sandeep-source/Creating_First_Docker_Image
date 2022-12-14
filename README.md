# Creating_First_Docker_Image
## Introduction

  Containers are amazing π€© and fun π. Creating a container and running βΆ your website π inside it just take few steps, But did π€ you know π§  how to create a custom container image. Creating a custom container has some more benifits over using existing one i.e you can show off π, you can share your project π or website which does not require any extra configutation β setup. In this repo i'm going πββοΈ to talk how to create your first container image with one  of the very famous container docker π³.  
  
## Pre-requisists
1. Docker π³ basics 
2. Familarity with command 
3. Nothing Else β

## First Step
  
  Very first 1οΈβ£ step πΆββοΈ to create a docker π³ image to install π  docker π³ . Most probably you had already done π this if you are reading this article, But if not checkout installation guide π [Here](https://docs.docker.com/engine/install).
  
## How to create one

 For creating images docker π³ provides `docker build` command. The syntax of docker π³ command as following
  
  ```
  docker build -t image_name dir_name
  ```
  
  Let's break down this command further
  
   1. `-t` flag is used to specify name of image.
   2. `image_name` is obiously value for `-t` flag - the name you want to give to your image
   3. `dir_name` is name of directory π in which docker is going to look π for a file named `Dockerfile` π€. It's our point of interest π€ to get to know how to creating a docker π³ image.
   
## What is Dockerfile π€

  Docker π³ reads instructions from Dockerfile to create an image. Basically Dockerfile specifies the step πΆββοΈ to take to create β a image according to your need.
  if you need more than one 1οΈβ£ file π for distict cases then use format `<word_of_choice>.Dockerfile`.
 
## Creating Dockefile
 
 ```Dockerfile
 FROM <base_image>
 ADD <src> <dest>
 COPY <src> <dest>
 EXPOSE <port>
 ENTRYPOINT <cmd>
 CMD <cmd>
 ```
 
 Let's take a look π at these commands
 1. `FROM` - It specifies the base image to be used. It forms base for our image. Our customization π§ will be placed on the top of this image. Base image can one the images available on dockerhub π³ which is bestfit for your usecase.
 2. `ADD` - It copies files π from source in host system π» to the destination of image to be created.
 3. `COPY` - It also copies files π from source in host system π» to the destination of image to be created.
 4. `EXPOSE` - This instruction is used to tell docker π³ to open a port inside container running βΆ this image.
 4. `ENTRYPOINT` - This specify command to be run βΆ, when image is used to run βΆ a container.
 5. `CMD` - This is also specifies command to run βΆ every time β² container run βΆ. `CMD` can be overriden when running βΆ image.
 
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
       
   2. Paste the following code π©βπ» inside file π
    
       ```Dockerfile
       FROM nginx
       ADD src/* /usr/share/nginx/html/
       EXPOSE 80
       CMD ["nginx","-g","daemon off;"]
       ```
      Let's break π¨ docker the following commands
        1. `FROM nginx` - This line tells docker π³ to use Nginx π as the official image as a base image for our new image.
        2. `ADD src/* /usr/share/nginx/html/` - This line copies files π of `src` folder inside the `/usr/share/nginx/html/` folder of image. `/usr/share/nginx/html/` folder is used by the nginx π server as entry point of website.
        3. ```EXPOSE 80``` - This line tells docker π³ to open port 80 inside the docker π³ container so that we can communicate with the nginx π server inside.
        4. ```CMD ["nginx","-g","daemon off;"]``` - This last cline starts Nginx π server and runs βΆ every time the docker π³ container start.
       
   3. Download the src folder π from this repo to your directory π
   4. Now your hackdir will look π like following
      
      ```
      hackdir/
         Dockerfile
         src/
            index.html
      ```
      
   6. Now run βΆ the following command
   
      ```
      docker build -t hackthenumber .
      ```
      
   5. To test your image run βΆ the following commands
   
      ```
      docker run -dp 80:80 hackthenumber
      ```
      
   6. Now visit the localhost. If everything done correctly you will see following output 
   
      ![Hack the number home screen](https://user-images.githubusercontent.com/61611561/202146123-80da9007-d472-48ce-ad0c-de3eab997eab.png)
      
## Conclusion 
   1. Building a container image can feel a litle bit anoying at very first 0οΈβ£ but after understanding some basic it will be piece of cake 
   2. It involve Three 3οΈβ£ step
      1. Create your application
      2. Create Dockerfile according to your need
      3. Run βΆ the docker build command

## Quick tools
 
 1. If you don't have docker π³ installed β or don't want to do, then try it from [Here](https://labs.play-with-docker.com/). Just login with dockerhub credentials and you are good to go.
 2. Try outout `Hack The Number` game from here π [Hack The Number](https://sandeep-source.github.io/Creating_First_Docker_Image/src/index.html).
 3. Got stuck at syntax errors? Try some Dockerfile validator like [FROM latest](https://www.fromlatest.io/)
     


