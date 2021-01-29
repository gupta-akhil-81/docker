# Docker Registry
It is a stateless, scalable application that stores and distribute docker images.
Registries could be local/private, or cloud-based.

* Docker Local Registry - open source registry
* DTR - Docker Trusted Registry
* Docker Hub - defualt cloud based registry from Docker.

## Local Open Source Registry 
> docker run -d -p 5000:5000 --restart=always --name myregistry registry:2
-d --> daemon
-p  --> port

It will start a container having registry application.

To publish an image into this local registry.
> docker tag ubuntu localhost:5000/ubuntu:myversion
> docker push ubuntu localhost:5000/ubuntu:myversion

To pull an image from local registry.
> docker pull ubuntu localhost:5000/ubuntu:myversion

To remove an image from local repository.
> docker image rm localhost:5000/ubuntu:myversion

## Docker Trsuted Registry 
It should be used for Production env.
* It gives GUI application.
* Can create multiple organizations
* It has secure image scanning
* etc..

## Docker Hub
This is default public cloud docker hub
