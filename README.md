# Docker Tutorial

To delete all containers including its volumes use,
```
docker rm -vf $(docker ps -a -q)
```

To delete all the images,
```
docker rmi -f $(docker images -a -q)
```


## How to build a docker image?

### What is different between ENV and ARG ?

<img src="./images/docker_environment_build_args.png" alt="Docker environment variables" width="300">

```
FROM ubuntu:20.04
ARG PROFILE
RUN echo START BUILDING IMAGE
RUN echo $PROFILE
```

```
docker build -t sample:1.0.0 .
docker build -t sample:1.0.1 .
```

Run the build command to build two image and you will see nothing run (WHILE USING RUN COMMAND) in second phase because it is using cache


```
docker build -t test:1.0.0 --build-arg PROFILE=dev .
docker build -t test:1.0.0 --build-arg PROFILE=stage .
docker build -t test:1.0.0 --build-arg PROFILE=prod .
```

Although this use same tag number it will not use the cache and it will create new image reagarding the conditions has been changed

## Volume

### Locating data volumes in Docker Desktop (Windows)

Windows + WSL 2
```
\\wsl$\docker-desktop-data\version-pack-data\community\docker\volumes\
```