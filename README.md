# hadoop-on-docker

Dockerfile for spark on hadoop, this repo build is mainly learn and copy from the [sequenceiq/hadoop docker repo](https://github.com/sequenceiq/hadoop-docker).

If you are interested in using this image, please refer to the customized [timmyraynor/hadoop-docker](https://hub.docker.com/r/timmyraynor/hadoop-docker/).

Or just use following command

```shell
  docker pull timmyarynor/hadoop-docker
 ```

The customizations are listed blow:
- based on ubuntu
- get latest hadoop stable 2.7.3
- use default ssh port 22 instead of the 2212 in the sequenceiq one

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

### exchange between hdfs & host

It is recommended to use some s3 like instance for the information exchange or just disk mount. In our case we use [*minio*](https://minio.io/):

```shell
  docker run -p 9000:9000 -e "MINIO_ACCESS_KEY=hello" -e "MINIO_SECRET_KEY=helloworld" minio/minio server /export
```

Then the GUI should be ready on port 9000. With the specified access_key and secret_key, your container can then setup a default .s3cfg file with the corresponding secret for connection.
  
