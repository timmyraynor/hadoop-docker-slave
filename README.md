# spark-on-hadoop-docker
Dockerfile for spark on hadoop, this repo build is mainly learn and copy from the [sequenceiq/hadoop docker repo](https://github.com/sequenceiq/hadoop-docker).

# how to run
simplest way to run is just
docker pull 

# shortcuts for deleting images and containers when you finished your customized build

```shell
  # Delete all containers
  docker rm $(docker ps -a -q)
  # Delete all images
  docker rmi $(docker images -q)
```
