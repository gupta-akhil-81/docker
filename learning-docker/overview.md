# Dcoker Overview
Docker uses client server architecture. 
- Docker Client
- Docker Deamon

Docker Client talks to daemon and issues commands to daemon. It talks over REST api.
Docker Daemon (dockerd) does the bulding and running of containers.
They both can run on same system.
Client can also connect to one or more remote Daemons.

Docker is written in Go language and it used *namespaces* to provide an isolated workspace called *container*.

# Docker Registeries
Stores docker images. 
Docker Hub is the public registry that anyone can use.
It is the by default registry.
We can use our own private registry also.
When use commands like `docker pull` ,  `docker run` or `docker push`  it always uses the configured or default registry.

# Images
It is a read only template having instructions for creating a Container.
Often an image is based on another image with some additional customization.
To create an image, we write a *Dockerfile*. Each instruction in the Dockerfile create a layer in the image. 
When a Dockerfile is changed and an image is rebuilt, only those layers are rebuilt which are changed. So image building is fast.
Image contains the container’s filesystem, it must contain everything needed to run an application - all dependencies, configuration, scripts, binaries, etc. The image also contains other configuration for the container, such as environment variables, a default command to run, and other metadata.

# Containers
These are runnable instance of images.
We can create, start, stop, move or delete a container.
Two containers are completely isolated from each other.

# Installing Docker Engine on one of the VM
Download and install containerd, docker-ce-cli and docket-engine.

> curl -o containerd.deb https://download.docker.com/linux/debian/dists/bullseye/pool/stable/amd64/containerd.io_1.6.4-1_amd64.deb
> 
> sudo dpkg -i containerd.deb
> 
>curl -o docker-ce-cli.deb https://download.docker.com/linux/debian/dists/bullseye/pool/stable/amd64/docker-ce-cli_20.10.9~3-0~debian-bullseye_amd64.deb
>
>sudo dpkg -i docker-ce-cli.deb 
>
> curl -o docker-engine.deb https://download.docker.com/linux/debian/dists/bullseye/pool/stable/amd64/docker-ce_20.10.9~3-0~debian-bullseye_amd64.deb
> 
> sudo dpkg -i docker-engine.deb

To test the installation, run following command. It will pull an image and run it and print a message.
> sudo docker run hello-world

There are other options to install container from registry or from ready-made Docker installation script.

# Sample Application 
Test with a sample To-Do list web app.
Donwload the sample app code:
> git clone https://github.com/docker/getting-started.git

Go to /app folder and create a Dockerfile with below contents:
```
# syntax=docker/dockerfile:1
FROM node:12-alpine
RUN apk add --no-cache python2 g++ make
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000
```

Build the image file using following command:
> docker build -t getting-started .

"-t" is to provide the tag name for the image.
"getting-started" is the tag name.

To see list of all images on your local system use following command:
> docker images
you must see the newly created image in the list.

Run a container from this image using the command:
> docker -dp 80:3000 getting-started

"-dp" means detached mode in the background and setting the port 30 on the host-VM to send requests to port 3000 in the container.
"getting-started"  is the name or tag of the image.

See list of running containers:
> docker stats 

or 

> docker ps

To stop the conatiner use following command:
> docker stop <<container_name>>

or 

> docker stop <<container_id>>

get the conatiner_name from the list of containers.

To remove the container from local system use follwing command:
> docker rm <<container_id>>

To stop and remove in one single command use following:
> docker rm -f <<container_id>>


# Docker Hub Repository - Default Docker Registry
Docker Hub is the default registry for Docker images.

## Login to your docker hub account using following command
> docker login -u <<user name>>
  
Create a repo in docker hub and make it public.

  
## Push the image of your app into your docker hub repository, so that it can be shared with others. 
> docker tag source_image[:tag_name] target_image[:tag_name]
>
> docker tag getting-started akhilgupta81/docker-getting-started
> 
> docker push image[:tage]
>
> docker push akhilgupta81/docker-getting-started
  
## Pull the image from a repo and run container from it
> docker login -u username
>
> docker pull image[:tag]
>
> docker pull akhilgupta81/docker-getting-started
>
> docker run -dp 80:3000 akhilgupta81/docker-getting-started
