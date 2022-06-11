---
title: Docker Cheetsheet 🐳
author: rexdivakar
date: 2022-02-10 20:47:00 +0800
categories: [containers, docker]
tags: [docker, cheetsheet, containers]
math: true
mermaid: true
toc: true # table of contents
comments: true
pin: false
---


Manage images
-------------

## docker build

Create an `image` from a Dockerfile.

```shell
docker build [options] .
  -t "app/container_name"    # name
  --build-arg APP_HOME=$APP_HOME    # Set build-time variables
```

## docker run

Deploys the container from `docker image`.

```shell
docker run [options] IMAGE
  # see `docker create` for options
```

### Example

Run a command in an `image`.

```shell
docker run -it debian:buster /bin/bash
```

Manage containers
-----------------

## docker Create

```yml
docker create [options] IMAGE
  -a, --attach               # attach stdout/err
  -i, --interactive          # attach stdin (interactive)
  -t, --tty                  # pseudo-tty
      --name NAME            # name your image
  -p, --publish 5000:5000    # port map (host:container)
      --expose 5432          # expose a port to linked containers
  -P, --publish-all          # publish all ports
      --link container:alias # linking
  -v, --volume `pwd`:/app    # mount (absolute paths needed)
  -e, --env NAME=hello       # env vars
```

#### Example

Create a `container` from an `image`.

```shell
$ docker create --name app_redis_1 \
  --expose 6379 \
  redis:3.0.2
```

### docker Exec

Command to login to the container,

```shell
docker exec [options] CONTAINER COMMAND
  -d, --detach        # run in background
  -i, --interactive   # stdin
  -t, --tty           # interactive
```

#### Example

Run commands in a `container`.

```shell
docker exec app_web_1 tail logs/development.log
docker exec -t -i app_web_1 rails c
```

### docker start/stop

Start/stop a `container`.

```shell
docker start [options] CONTAINER
  -a, --attach        # attach stdout/err
  -i, --interactive   # attach stdin

docker stop [options] CONTAINER
```

### docker ps

Manage `container`s using ps/kill.

```shell
docker ps
docker ps -a
docker kill $ID
```

### docker logs

See what's being logged in an `container`.

```shell
docker logs $ID
docker logs $ID 2>&1 | less
docker logs -f $ID # Follow log output
```

Images
------

### docker images

Manages `image`s.

```shell
$ docker images
  REPOSITORY   TAG        ID
  ubuntu       12.10      b750fe78269d
  me/myapp     latest     7b2431a8d968
```

```shell
docker images -a   # also show intermediate
```

### docker rmi

Deletes `image`s.

```shell
docker rmi b750fe78269d
```

## Clean up

### Clean all

Cleans up dangling images, containers, volumes, and networks (ie, not associated with a container)

```shell
docker system prune
```

Additionally remove any stopped containers and all unused images (not just dangling images)

```shell
docker system prune -a
```

### Containers

```shell
# Stop all running containers
docker stop $(docker ps -a -q)

# Delete stopped containers
docker container prune
```

### Images

Delete all the images

```shell
docker image prune [-a]
```

### Volumes

Delete all the volumes

```shell
docker volume prune
```

## Sevices

To view list of all the services runnning in swarm

```shell
docker service ls 

```

To see all running services

```shell
docker stack services stack_name
```

to see all services logs

```shell
docker service logs stack_name service_name 
```

To scale services quickly across qualified node

```shell
docker service scale stack_name_service_name=replicas
```

### Clean up

To clean or prune unused (dangling) images

```shell
docker image prune 
```

To remove all images which are not in use containers , add - a

```shell
docker image prune -a 
```

To prune your entire system

```shell
docker system prune 
```

To leave swarm

```shell
docker swarm leave  
```

To remove swarm ( deletes all volume data and database info)

```shell
docker stack rm stack_name  
```

To kill all running containers

```shell
docker kill $(docekr ps -q ) 
```

Also see
--------

* [Getting Started](http://www.docker.io/gettingstarted/) _(docker.io)_
