# [Docker](https://www.docker.com/)

List all containers:

```bash
docker ps --all
```

Note: Remove `--all` option to only list containers that are running.

Stop all running containers:

```bash
docker stop $(docker ps -aq)
```

Remove all containers:

```bash
docker rm $(docker ps -aq)
```

List images (no intermediates):

```bash
docker images
```

Note: Add `--all` option to include intermediate images.

Remove all images:

```bash
docker rmi $(docker images -q)
```

Delete all unused volumes:

```bash
docker volume prune --force
```

Delete all unused networks:

```bash
docker network prune --force
```
