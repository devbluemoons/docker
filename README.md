## install

```console
# macOS (Docker Desktop)

# remove 
brew remove docker

# install docker desktop
brew install --cask docker

# install docker command line
brew install docker

# version check
docker version
```

## run
```console
# start Docker Desktop on "macOS"
open -a Docker
```

## command

- [x] **docker container**

`run`  :  download image and run
```console
# run [image-name]
docker container run nginx
```

`top`  :  output running process list
```console
# top [part of Container-ID from first character]
docker container top abc123
```

`log`  :  output collected all log
```console
# log [part of Container-ID from first character]
docker container log abc123
```

`inspect`  :  output detail container information
```console
# inspect [part of Container-ID from first character]
docker container inspect abc123
```

`stats`  :  output running container state
```console
# stats [part of Container-ID from first character]
docker container stats abc123
```

`rm`  :  output running container state
```console
# rm [part of Container-ID from first character or all]
docker container rm --force $(docker ps --all --quiet)
```

`cp`  :  copy file or directory
```console
# rm [part of Container-ID from first character or all]
docker container rm --force $(docker ps --all --quiet)
```

- [x] **docker image**

`pull`  :  pull image
```console
docker image pull [image-name]
```

`push`  :  push image
```console
docker image push [image-name]
```

`build`  :  build image
```console
docker image build [image-name] --tag abc123
```

`history`  :  output container-image history information
```console
docker image history [image-name]
```

- [x] **docker system**

`df`  :  output system information
```console
docker system df
```

- [x] **docker network**

`create`  :  create network
```console
docker network create [network-name]
```

- [x] **docker  volume**

`create`  :  create volume
```console
docker volume create [volume-name]
```

- [x] **DockerHub Login**
```console
docker login --username [docker-id]
```

## flag
`--interactive`  :  connected state
```console
# docker container run --interactive [image-name]
docker container run --interactive havi-apps
```

`--tty`  :  control with session
```console
# docker container run --tty [image-name]
# docker container run --tty havi-apps
```

`--all`  :  all of result list
```console
docker ps --all
```

`--detach | -d`  :  Running containers in the background
```console
docker container run --detach [host-port:container-port] [image-name]
docker container run --detach 8080:80 havi-apps
```

`--publish | -p`  :  Open container port to host
```console
docker container run --publish [host-port:container-port] [image-name]
docker container run --publish 8080:80 havi-apps
```

`--force | -f`  :  forced action
```console
docker container rm --force abc123
```

`--quiet`  : 
```console
docker container --quiet
```

`--name`  :  set name to container
```console
docker container run --name demo abc123
```

`--env`  :  set environment variable
```console
docker container run --env NAME=demo
```

`--tag`  :  set build image name
```console
docker image build --tag demo .
```

## common pattern 
```console
# case01
docker container run --interactive --tty [image-name]

# case02
docker container run --detach --publish [host-port:container-port] [image-name]

# case03
docker container rm --force $(docker ps --all --quiet)
```

## Dockerfile
- script for application packaging

```dockerfile
# set image-name
FROM havi-apps

# work directory
WORKDIR /dev

# command to do
CMD ["go", "/dev/main.go"] 

# environment variable
ENV DESCRIPTION="programming language" \
    SUPPORT="google" \
    NAME="go"

# copy file or direactory to container image
COPY main.go .
```
