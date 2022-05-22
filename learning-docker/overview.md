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
> sudo dpkg -i containerd.deb
>curl -o docker-ce-cli.deb https://download.docker.com/linux/debian/dists/bullseye/pool/stable/amd64/docker-ce-cli_20.10.9~3-0~debian-bullseye_amd64.deb
>sudo dpkg -i docker-ce-cli.deb 
> curl -o docker-engine.deb https://download.docker.com/linux/debian/dists/bullseye/pool/stable/amd64/docker-ce_20.10.9~3-0~debian-bullseye_amd64.deb
> sudo dpkg -i docker-engine.deb

To test the installation, run following command. It will pull an image and run it and print a message.
> sudo docker run hello-world

There are other options to install container from registry or from ready-made Docker installation script.
