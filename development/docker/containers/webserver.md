# Running web server

- [Image vs. Container](#image-vs-container)
- [docker container run](#docker-container-run)
- [docker container ls](#docker-container-ls)
- [docker container stop](#docker-container-stop)
- [docker container start](#docker-container-start)
- [docker container logs](#docker-container-logs)
- [docker container top](#docker-container-top)
- [docker container rm](#docker-container-rm)

## Image vs. Container

Image
: the application we want to run

Container
: an instance of the image running as a process

Multiple containers can be running off the same image.

Docker's default image "registry" is a [Docker Hub](https://hub.docker.com/)

## docker container run

starts a *new* container from an image

`docker run` (old way)

```console
user@host:~$ docker container run --publish 8080:80 nginx
```

1. downloaded image 'nginx' from Docker Hub
2. started a new container from the image
3. opened port 8080 on the host IP
4. routes that traffic to the container IP, port 80

with **--detach** or **-d** parameter command runs container in the background, and the `docker container run` command returns unique container's id.

```console
user@host:~$ docker container run --publish 8080:80 --detach nginx
5d91d866d7de3f543ac25dfb28e74a4cdd918a80637f1e35f76874cb8e1bb7c3
```

with **--name** or **-n** parameter command assign specified name to a container. Containers get some randomized names unless we specify them directly.

```console
user@host:~$ docker container run --publish 8080:80 --detach --name webhost nginx
fc46fb7f4522608a435bab0a511a15076ae507cf588a929e51746aa1b3ab3d3d
user@host:~$ docker container ls
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS                      PORTS                  NAMES
fc46fb7f4522   nginx     "/docker-entrypoint.…"   13 seconds ago   Up 12 seconds               0.0.0.0:8080->80/tcp   webhost
```

## docker container ls

list running containers

`docker container ls`

`docker ps` (old way)

```console
user@host:~$ docker container ls
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS                  NAMES
5d91d866d7de   nginx     "/docker-entrypoint.…"   2 minutes ago   Up 2 minutes   0.0.0.0:8080->80/tcp   sharp_agnesi
```

with **-a** parameter command lists all containers, including stopped ones

```console
user@host:~$ docker container ls -a
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS                      PORTS     NAMES
c1378e809d50   nginx     "/docker-entrypoint.…"   14 minutes ago   Exited (0) 14 minutes ago             modest_keller
4a05b258bf51   nginx     "/docker-entrypoint.…"   14 minutes ago   Exited (0) 14 minutes ago             kind_sinoussi
```

## docker container stop

stops the container process but doesn't remove it

`docker container stop CONTAINER`

`docker stop CONTAINER` (old way)

```console
user@host:~$ docker container stop 5d9
5d9
user@host:~$ docker container ls
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

`CONTAINER` can be

- container's id (can be first several characters that can uniquely distinguish the container)
- container's name

## docker container start

starts an existing stopped container

`docker container start CONTAINER`

```console
user@host:~$ docker container ls -a
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS                      PORTS     NAMES
fbbd240b1b70   nginx     "/docker-entrypoint.…"   32 seconds ago   Exited (0) 23 seconds ago             webhost
user@host:~$ docker container start webhost
webhost
user@host:~$ docker container ls
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS         PORTS                  NAMES
fbbd240b1b70   nginx     "/docker-entrypoint.…"   44 seconds ago   Up 2 seconds   0.0.0.0:8080->80/tcp   webhost
```

## docker container logs

shows logs for a specific container

`docker container logs CONTAINER`

`docker logs CONTAINER` (old way)

```console
user@host:~$ docker container logs webhost
172.17.0.1 - - [23/Jan/2024:12:33:03 +0000] "GET / HTTP/1.1" 304 0 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36" "-"
172.17.0.1 - - [23/Jan/2024:12:33:05 +0000] "GET / HTTP/1.1" 304 0 "-" "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36" "-"
```

## docker container top

displays the running processes of a container

`docker container top CONTAINER`

```console
user@host:~$ docker container top webhost
UID                 PID                 PPID                C                   STIME               TTY                 TIME                CMD
root                2480                2458                0                   12:29               ?                   00:00:00            nginx: master process nginx -g daemon off;
_rpc                2530                2480                0                   12:29               ?                   00:00:00            nginx: worker process
```

## docker container rm

removes one or more containers, does not remove running containers by default (use **-f** to force deleting running containers)

`docker container rm CONTAINER`

`docker rm CONTAINER` (old way)

```console
user@host:~$ docker container ls -a
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS                      PORTS                  NAMES
fc46fb7f4522   nginx     "/docker-entrypoint.…"   11 minutes ago   Up 11 minutes               0.0.0.0:8080->80/tcp   webhost
5d91d866d7de   nginx     "/docker-entrypoint.…"   30 minutes ago   Exited (0) 21 minutes ago                          sharp_agnesi
user@host:~$ docker container rm fc4 5d9
5d9
Error response from daemon: You cannot remove a running container fc46fb7f4522608a435bab0a511a15076ae507cf588a929e51746aa1b3ab3d3d. Stop the container before attempting removal or force remove
user@host:~$ docker container ls -a
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                  NAMES
fc46fb7f4522   nginx     "/docker-entrypoint.…"   12 minutes ago   Up 12 minutes   0.0.0.0:8080->80/tcp   webhost
user@host:~$ docker container rm -f fc4
fc4
user@host:~$ docker container ls -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```
