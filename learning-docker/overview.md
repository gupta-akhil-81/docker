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

# Containers
These are runnable instance of images.
We can create, start, stop, move or delete a container.
Two containers are completely isolated from each other.
