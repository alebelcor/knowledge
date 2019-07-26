# [Docker](https://www.docker.com/)

Stop all running containers:

```bash
docker stop $(docker ps -aq)
```

Remove all containers:

```bash
docker rm $(docker ps -aq)
```

Remove all images:

```bash
docker rmi $(docker images -q)
```

Delete a volume:

```bash
docker volume rm <volume name>
```
