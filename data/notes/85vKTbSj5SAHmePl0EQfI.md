
## Overview
_NetworkChuck_ (Youtube Channel)

In usual virtualisation, the operating systems are built on top of a hypervisor which is essentially virtualising the hardware.

With **Docker**, the an a _Docker Engine_ runs on top an existing operating system. In this case it is the OS which is virtualised, rather than the hardware. These run as isolated containers, are lightweight and fast.

![](/assets/images/2022-01-16-08-59-02.png)
https://www.youtube.com/watch?v=eGz9DS-aIeY

The reason why Docker containers are so fast is they share the kernel with the underlying operating system instead of rebuilding the kernel for each container. The drawback to this is a Linux Docker container will not run on a Windows OS and vice versa.

## Basic Docker commands

```bash

# to launch a container with an OS of choice
docker pull centos
docker run -d -t --name <the-container-name> centos

# view all current running containers
docker ps

# enter into container and launch bash shell
docker exec -it <the-container-name> bash

# stop & start a container
docker stop <the-container-name>
docker start <the-container-name>

# view container performance: memory, CPU etc
docker stats

# remove a container
docker rm <the-container-name>

# login in to repo
docker login -u YOUR-USER-NAME

# tag a container image to match repo
docker tag <the-container-name> YOUR-USER-NAME/<repo-name>

# list all container ids
docker ps -aq

# kill all running containers (bash)
docker stop $(docker ps -aq)

# removal all containers
docker rm $(docker ps -aq)

# cleanse docker, removing images & containers
docker system prune

```

## Building an app container
1. Create a file called `Dockerfile` (typically in the root directory of a project)
2. Fill `Dockerfile` with juicy instructions
3. Build container image, using command `docker build -t <image-name> .`
    - `t` flag tags the image
    - the `.` tells Docker to look for the `Dockerfile` in the current directory
4. Run docker container `docker run -dp 3000:3000 <image-name>`
    - `d` flag is detached mode (in the background)
    - `p` is referring to the port mapping, in this case `3000:3000`
    









