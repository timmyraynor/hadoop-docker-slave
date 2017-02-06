# spark-on-hadoop-docker

Dockerfile for spark on hadoop, this repo build is mainly learn and copy from the [sequenceiq/hadoop docker repo](https://github.com/sequenceiq/hadoop-docker).

# how to run

Simplest way to run is using `docker build  -t hadoop-docker:latest .` to build. Then you could  use `docker run -it -d -P hadoop-docker` to get the system running.

You will also need `docker port <container id or name>` to tell the port mapping after the `-P` option.

The *bootstrap.sh* script is the default entry point for this docker image. You can also specifically call the *bootstrap.sh* script like following.

```shell
docker run -it -d hadoop-docker:latest /etc/bootstrap.sh -bash
```

# misc

### shortcuts for deleting images and containers when you finished your customized build

```shell
  # Delete all containers
  docker rm $(docker ps -a -q)
  # Delete all images
  docker rmi $(docker images -q)
```
