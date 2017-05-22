# DOCKER

### Installation (Ubuntu)
===
```sh
# check the kernel supports docker (greather than v3.1)
$ uname -r

$ sudo apt update
$ sudo apt install docker-engine
$ sudo service docker start

# test docker-engine
$ sudo docker run hello-world
```

### 1. Basic Bash commands
===
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

### Create containers
===

### Setup MySql Server using Docker container
```sh
# download container image from docker hub
docker pull mysql/mysql-server:5.6
docker pull mysql/mysql-server:5.7

# display images on local machine
docker images

# create and run docker container
# ------
docker run --name my-container-name -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql/mysql-server:tag

# use datadir on host
docker run --name my-container-name -v /host/datadir:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql/mysql-server:tag

# use password in text file on host
docker run --name my-container-name -e MYSQL_ROOT_PASSWORD=/tmp/password.txt -v /host/password.txt:/tmp/password.txt  -d mysql/mysql-server:tag  

# use datadir and password text file on host, and forward container port 3306 to host port 3306
docker run --name my-container-name -v /host/datadir:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=/tmp/password.txt -v /host/password.txt:/tmp/password.txt -p 3306:3306 -d mysql/mysql-server:5.6



# check that container was created and running
docker ps  -a

# connect to mysql client inside container
docker exec -it my-container-name mysql -uroot -p


# link another app to mysql container (if port forwarding was not activated)
docker run --name app-container-name --link my-container-name:mysql -d app-that-uses-mysql


```

