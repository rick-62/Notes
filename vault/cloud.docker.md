---
id: 85vKTbSj5SAHmePl0EQfI
title: Docker
desc: ''
updated: 1642325694056
created: 1642323476642
---

## Overview
_NetworkChuck_ (Youtube Channel)

In usual virtualisation, the operating systems are built on top of a hypervisor which is essentially virtualising the hardware.

With **Docker**, the an a _Docker Engine_ runs on top an existing operating system. In this case it is the OS which is virtualised, rather than the hardware. These run as isolated containers, are lightweight and fast.

![](/assets/images/2022-01-16-08-59-02.png)
https://www.youtube.com/watch?v=eGz9DS-aIeY

The reason why Docker containers are so fast is they share the kernel with the underlying operating system instead of rebuilding the kernel for each container. The drawback to this is a Linux Docker container will not run on a Windows OS and vice versa.

## Docker CLI

```bash

# to launch a container with an OS of choice
docker pull centos
docker run -d -t --name anycontainername centos

# view all current running containers
docker ps

# enter into container and launch bash shell
docker exec -it anycontainername bash

# stop & start a container
docker stop anycontainername
docker start anycontainername

# view container performance: memory, CPU etc
docker stats

```








