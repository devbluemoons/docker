
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

`run` : download image and run
```console
# run <image-name>
docker container run nginx
```

`top` : output running process list
```console
# top <part of Container-ID from first character>
docker container top abc123
```

`log` : output collected all log
```console
# log <part of Container-ID from first character>
docker container log abc123
```

`inspect` : output detail container information
```console
# inspect <part of Container-ID from first character>
docker container inspect abc123
```

`stats` : output running container state
```console
# stats <part of Container-ID from first character>
docker container stats abc123
```

`rm` : output running container state
```console
# rm <part of Container-ID from first character or all>
docker container rm --force $(docker ps --all --quiet)
```
`exec` : execute command to container that is already running
```console
# exec <part of Container-ID from first character or all>
docker container exec ls /usr/local/apache2/htdocs
```

`cp` : copy file or directory
```console
# rm <part of Container-ID from first character or all>
docker container rm --force $(docker ps --all --quiet)
```

- [x] **docker image**

`pull` : pull image
```console
docker image pull <image-name>
```

`push` : push image
```console
docker image push <image-name>
```

`build` : build image
```console
docker image build <image-name> --tag abc123
```

`history` : output container-image history information
```console
docker image history <image-name>
```

- [x] **docker system**

`df` : output system information
```console
docker system df
```

- [x] **docker network**

`create` : create network
```console
docker network create <network-name>
```

- [x] **docker  volume**

`create` : create volume
```console
docker volume create <volume-name>
```

- [x] **DockerHub Login**
```console
docker login --username <docker-id>
```

## flag
`--interactive` : connected state
```console
# docker container run --interactive <image-name>
docker container run --interactive havi-apps
```

`--tty` : control with session
```console
# docker container run --tty <image-name>
# docker container run --tty havi-apps
```

`--all` : all of result list
```console
docker ps --all
```

`--detach | -d` : Running containers in the background
```console
docker container run --detach <host-port:container-port> <image-name>
docker container run --detach 8080:80 havi-apps
```

`--publish | -p` : Open container port to host
```console
docker container run --publish <host-port:container-port> <image-name>
docker container run --publish 8080:80 havi-apps
```

`--force | -f` : forced action
```console
docker container rm --force abc123
```

`--quiet` : 
```console
docker container --quiet
```

`--name` : set name to container
```console
docker container run --name demo abc123
```

`--env | -e` : set environment variable
```console
docker container run --env NAME=demo
```

`--tag | -t` : set build image name
```console
docker image build --tag demo .
```

## common pattern 
```console
# case01 (interactive + tty)
docker container run -it <image-name>

# case02 (detach + publish)
docker container run -dp <host-port:container-port> <image-name>

# case03 (force / all + quiet)
docker container rm -f $(docker ps -aq)
```

## Dockerfile
- script for application packaging

```dockerfile
# set image-name & alias
FROM havi-apps AS demo

# execute command while building container and save a result to image layer
RUN echo "test" > /test.txt

# change directory
WORKDIR <directory to change>

# command to do
CMD ["go", "/dev/main.go"]

# export port number
EXPOSE <port-number>

# command to do
ENTRYPOINT <your-command>

# environment variable
ENV DESCRIPTION="programming language" \
    SUPPORT="google" \
    NAME="go"

# 
VOLUME <target-directory>

# copy file or directory to container image
COPY main.go .
```
