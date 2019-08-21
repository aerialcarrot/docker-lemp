# LEMP for Docker
A clustered LEMP example running on Docker. Contains 3 node Nginx cluster with PHP and MySQL served by Traefik proxy/LB.

## Prerequisites
The following software is required before running LEMP for Docker:
- [Docker](https://docs.docker.com/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Install
To build and start the complete stack simply run the following:
```
$ git clone git@github.com:markolly/docker-lemp.git
$ cd docker-lemp
$ docker-compose up -d
```
Containers can be checked for their current state by running:
```
$ docker ps
```

## Accesing sites
Traefik has been set up to use name-based virtual hosting. Once the stack is up and running sites will be available at the following locations:

-  Traefik LB - http://traefik.docker.localhost
-  Nginx site - http://nginx.docker.localhost
-  phpMyAdmin - http://pma.docker.localhost (Server:mysql, Username:project, Password:project)

## Updating a container
The majority of the images used in the stack are pulled straight from Docker Hub apart from the PHP container. This is built from its own Dockerfile located at docker/php/Dockerfile. If you wanted to upgrade PHP from 5.6 to 7.2, changes are made in the Dockerfile and then the following docker-compose command can be run to update the PHP container without having reload the entire stack. 
```
$ docker-compose up -d --build --no-deps php
```
## Uninstall
To stop all "LEMP for docker" containers and delete them run: 
```
$ docker-compose down 
```
