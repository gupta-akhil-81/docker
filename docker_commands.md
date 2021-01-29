
# To get all information of a docker installation
> docker info


> docker version

Login in the docker host
> docker login

To pull a new image from the docker registry
> docker pull <image name>

Get the list of all images in the docker engine
> docker images   --> deprecated
> docker image ls

Tag a image on your local
> docker tag <image_id> <docker_id>/<image_name>:<tag_name>
When you tag, the image remain same.

To push a repository and all its tags into your docker registry.
> docker push <docker_id>/<repository_name>:<tag_name>
e.g.
> docker push akhilgupta81/alpine:myalpine

To delete a docker image from local
> docker image rm <image_id>
> -f --> for force delete


To clan the all the images from the local repository. It removes all unused images. i.e. not used by any container
> docker image prune -a

To see all current/history containers.
> docker container ls -a

To see what containers are running now
> docker ps

To see all containers even those which are existed
> docker ps -a

To be run on a Manager node. It gives status of all nodes in a Docker Swarm Cluster
> docker node ls 

To see logs of a docker container
> docker logs <container_id>