<!--
 * @Author: your name
 * @Date: 2020-09-24 17:24:33
 * @LastEditTime: 2020-09-25 00:25:13
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: /Learning_Docker-Linkedin_Learning/Notes.md
-->
Which statement best describes Docker containers?
    - They are sealed, self-contained units of software that have everything needed to run a service.

Boot2Docker is considered too old to support modern Docker functionality, remove it before installation if you have it.


1. Setting up Docker
    install docker:
        1) Mac and Windows: Download from the docker official web
        2) Linux: Follow commands on docker official web, there are several steps

    allow non-root users to run Docker as well on Linux:
        $ sudo groupadd docker
        $ sudo usermod -aG docker <Username>
        Log out and then log in back again.

    run container:
        $ docker run <container Name>   <!--Run local container or from network-->
        $ docker run hello-world        <!--From the internet, to test docker-->

    check docker info:
        $ docker info


2. Using docker
    check images:
        $ docker images     <!--ID is the easiest to visit a image -->
    
    run and interact with iamge:
        $ docker run -i -t <image> bash      <!--i: interactive, t: terminal, bash: run bash shell in image-->
        or $ doker run -it <iamge> bash
        $ exit                  <!-- exit the image-->

    Docker Image vs. Docker Container:
        Reference: https://phoenixnap.com/kb/docker-image-vs-container
        
        Iamge: 
        A Docker image is an immutable (unchangeable) file that contains the source code, libraries, dependencies, tools, and other files needed for an application to run. 
        Since images are, in a way, just templates, you cannot start or run them. What you can do is use that template as a base to build a container.
        Once you create a container, it adds a writable layer on top of the immutable image, meaning you can now modify it.
        You can create an unlimited number of Docker images from one image base. Each time you change the initial state of an image and save the existing state, you create a new template with an additional layer on top of it.

        Container: 
        A Docker container is a virtualized run-time environment where users can isolate applications from the underlying system. 
        As containers are autonomous, they provide strong isolation, ensuring they do not interrupt other running containers, as well as the server that supports them.

        Containers are runnning images, or started from images. Images are fixed that won't be changed. Inside a container, whatever changes you made, once you exit and re-start from the same image(we are in a new container now), nothing will be changed.
        Images can exist without containers, whereas a container needs to run an image to exist. Therefore, containers are dependent on images and use them to construct a run-time environment and run an application.

        Image  ==docker run==>  Running container  ==exit==> Stopped container ==docker commit==> New image


    check running containers(containers are running images):
    container's ID is different from image ID
        $ docker ps

    check all containers(running and stopped)
        $ docker ps -a

    check last container to exit:
        $ docker ps -l

    create a new image based on stopped container:
        $ docker ps -l  <!--To get the stopped container's ID-->
        $ docker commit <target container ID>   <!--You will get the ID of new image-->
        $ docker tag <new image ID> <name of new image>

        or we can simply do this:
        $ docker commit <NAME of target container> <name of new image>
        

