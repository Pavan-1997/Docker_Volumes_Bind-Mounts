# Docker_Volumes_Bind-Mounts

It is a very common requirement to persist the data in a Docker container beyond the lifetime of the container. However, the file system of a Docker container is deleted/removed when the container dies.

There are 2 different ways how docker solves this problem.

Volumes
Bind Directory on a host as a Mount
