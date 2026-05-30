# Java environment on Docker

[![MIT License](https://img.shields.io/github/license/lentiancn/docker-gentkit-java.svg?style=flat-square&label=license)](LICENSE)
[![GitHub Release](https://img.shields.io/github/tag/lentiancn/docker-gentkit-java.svg?style=flat-square&label=release)](https://github.com/lentiancn/docker-gentkit-java/releases)

A project for building Docker image based on Java environment .

## Supported tags

### based on Debian Linux (gentkit/debian:latest)

[latest]()
[openjdk-slim]()
[21-openjdk-slim]()
[17-openjdk-slim]()
[11-openjdk-slim]()
[8-openjdk-slim]()

### based on Alpine Linux (gentkit/alpine:latest)

[openjdk-alpine]()
[21-openjdk-alpine]()
[17-openjdk-alpine]()
[11-openjdk-alpine]()
[8-openjdk-alpine]()

## Pull and run into a new container

```shell
docker run -it \
--name <CONTAINER_NAME> \
gentkit/java:<TAG_NAME>
```

## Exec into your running container

```shell
docker exec -it \
<CONTAINER_NAME_OR_ID> \
/bin/sh
```

**NOTE** : Check status and start it using :
**docker ps -a --filter "name=<CONTAINER_NAME>"** and
**docker start <CONTAINER_NAME_OR_ID>**

## License

**gentkit/java** is licensed under
the [MIT License](LICENSE) .
