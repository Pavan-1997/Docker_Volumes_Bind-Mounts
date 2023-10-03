# Docker_Volumes_Bind-Mounts

It is a very common requirement to persist the data in a Docker container beyond the lifetime of the container. However, the file system of a Docker container is deleted/removed when the container dies.

There are 2 different ways how docker solves this problem.

- Volumes
- Bind Directory on a host as a Mount

Volumes aims to solve the same problem by providing a way to store data on the host file system, separate from the container's file system, so that the data can persist even if the container is deleted and recreated.

![image](https://github.com/Pavan-1997/Docker_Volumes_Bind-Mounts/assets/32020205/8c9bd3af-3e7a-4f8e-a5d9-bec833abe381)
