# Docker

- [Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)
- [Control Docker with systemd](https://docs.docker.com/config/daemon/systemd/)

## [docker run](https://docs.docker.com/engine/reference/commandline/run/)

```bash docker
# With env file

# Add volume
docker run -v /etc/letsencrypt:/etc/letsencrypt hello-world

# Define port
docker run -p 443:443 -p 2195:2195 -p 2196:2196 -p 2197:2197 -p 2198:2198 -p 5223:5223 hello-world
```

## [docker port](https://docs.docker.com/engine/reference/commandline/port/)

```bash
# docker port
docker port <container ID> 80
```

## docker logs

- [View logs for a container or service](https://docs.docker.com/config/containers/logging/)
- [Configure logging drivers](https://docs.docker.com/config/containers/logging/configure/)
-

## volume

- [Use volumes](https://docs.docker.com/storage/volumes/)

## network

- [Can't ping service inside Docker container from the host machine](https://stackoverflow.com/questions/68712773/cant-ping-service-inside-docker-container-from-the-host-machine)

## [Docker Compose](https://docs.docker.com/compose/)

## Troubleshoot

- [File not found in docker container](https://stackoverflow.com/questions/36001786/file-not-found-in-docker-container)
- [How to Fix Docker Permission Denied Error on Ubuntu](https://linuxhandbook.com/docker-permission-denied/#:~:text=deal%20with%20it.-,Fix%201%3A%20Run%20all%20the%20docker%20commands%20with%20sudo,the%20Docker%20daemon%20socket'%20anymore.)
