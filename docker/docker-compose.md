# [Docker Compose](https://docs.docker.com/compose/)

## [docker compose up](https://docs.docker.com/engine/reference/commandline/compose_up/)

Build environment from `docker-compose.yaml` and start service.

```shell
# Start docker compose with project name and run in background
docker compose -p example-project up --detach
```

## [docker compose stop](https://docs.docker.com/engine/reference/commandline/compose_stop/)

Stop containers and services define from `docker-compose.yaml`.

```shell
# Stop docker services with project name
docker compose -p example-project stop
```

## [docker compose down](https://docs.docker.com/engine/reference/commandline/compose_down/)

Stop services and erase environment built at `docker compose up`.

```shell
# Erase environment
docker compose -p example-project stop
```
