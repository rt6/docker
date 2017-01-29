#Docker Cheatsheet#
---

##Start and Stop Containers
---

Docker Command| Example | Description 
---|--- | ---
docker [command] --help | docker run --help | display command help and parameters
docker images || display current images
docker search [image name] | docker search mongo | search for docker image
docker pull [image name] | docker pull mongo | download docker image
docker run --name [instance name] -d [image name] | docker run --name mongo-database -d mongo | create container and detach
docker ps -a | | display all running containers
docker stop [container name] | docker stop mongo-db | stop container
docker rm [container name] | docker rm mongo-db | delete container
docker exec -it [containerID] bash | docker exec -it abc0123 bash | connect to bash cli inside container

## Build Container Images
---
Docker Command| Example | Description 
---|--- | ---
docker build -t [name]/[tag] . | docker build -t node/my-app . | Create docker image from Dockerfile
