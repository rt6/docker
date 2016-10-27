# DOCKER

1. Basic Bash commands
```sh
docker --version
docker-compose --version

# test that docker is working properly
docker run hello-world

# see what containers are running
docker ps

# run docker container with nginx at port 80.  The docker container name is webserver
# docker will download the image if it not available locally
docker run -d -p 80:80 -name webserver nginx

# start and stop a docker container
docker stop webserver
docker start webserver

# kill docker container. (kill webserver that was created above)
docker rm -f webserver

# list docker images
docker images

# delete docker image
docker rmi <imageID> 
docker rmi <imageName>
docker rmi nginx

```
