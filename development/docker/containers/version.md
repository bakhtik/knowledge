# Check out docker install and config

1. [docker command line structure](#docker-command-line-structure)
2. [docker](#docker)
3. [docker version](#docker-version)
4. [docker info](#docker-info)

## docker command line structure

- old: ```docker <command> (options)```
- new: ```docker <command>  <sub-command> (options)```

## docker

show list of commands

```console
user@host:~$ docker
Usage:  docker [OPTIONS] COMMAND
A self-sufficient runtime for containers

Management Commands:
  config      Manage Docker configs
  container   Manage containers

Commands:
  attach      Attach local standard input, output, and error streams to a running container
  build       Build an image from a Dockerfile
```

## docker version

check your version and that docker is working

```console
user@host:~$ docker version
Client: Docker Engine - Community
 Cloud integration: v1.0.29
 Version:           20.10.22

Server: Docker Desktop 4.15.0 (93002)
 Engine:
  Version:          20.10.21
```

## docker info

shows most configuration values for the engine

```console
user@host:~$ docker info
Client:
 Context:    desktop-linux

Server:
 Containers: 0
  Running: 0
 Images: 12
 Server Version: 20.10.21
 ```
