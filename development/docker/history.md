# History of Docker

## Background

Technology has emerged on 1970s with introducing JAIL on UNIXv7 operating systems by DEC.

With the help of "chroot" operation JAIL isolates process in own virtual file system, so that the process don't know about the root file system of the host machine.

In the first decade of 2000s the containerization-related technologies rapidly invented:

- 2004: **cgroups** for time-based processes multiplexing by Google
- 2006: **namespaces** for limiting root access in containers by RedHat
- 2008: **LXC** container's management tools and ecosystem by IBM

All these finally combined into **Docker** - simple and convenient container management ecosystem.

Docker underlying technology evolution:

1. Shell scripts
2. Python
3. Golang

In some sense Golang own his success to the success of Docker.

## Docker components

- **Docker Daemon:** Manages containers' lifecycle, connects services with each other
- **Docker Engine**
- **Dockerfile**
- **Images**
- **Containers**
- **Volumes**

## Dockerfile

- Recipe for image creation
- One line - one command
- Base image is a foundation layer of the docker image
- Static (infrequently changing) layers are placed at the top of the Dockerfile, while dynamic ones - close to the bottom. The reason is to eliminate rebuilding static layers. If hashed layer is stays below un-hashed one, it will be forced to rebuild.

Best practice:

- Stateful app - use fully fledged virtual machine
- Stateless app - feel free to use Docker container

One of the big issue related to the Docker containers is a relatively weak security: core isolation is under the question.
