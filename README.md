# Docker_Volumes_Bind-Mounts

## Docker Volumes

It is a very common requirement to persist the data in a Docker container beyond the lifetime of the container. However, the file system of a Docker container is deleted/removed when the container dies.

There are 2 different ways how docker solves this problem.

- Volumes
- Bind Directory on a host as a Mount

Volumes aims to solve the same problem by providing a way to store data on the host file system, separate from the container's file system, so that the data can persist even if the container is deleted and recreated.

![image](https://github.com/Pavan-1997/Docker_Volumes_Bind-Mounts/assets/32020205/8c9bd3af-3e7a-4f8e-a5d9-bec833abe381)

Volumes can be created and managed using the docker volume command. You can create a new volume using the following command:

```
docker volume create <volume_name>
```

Once a volume is created, you can mount it to a container using the -v or --mount option when running a docker run command. 

```
docker run -it -v <volume_name>:/data <image_name> /bin/bash
```
`This command will mount the volume <volume_name> to the /data directory in the container. Any data written to the /data directory
inside the container will be persisted in the volume on the host file system.`

### Below are a few more commands related to docker volumes:

```
docker volume ls
```
`To view all volumes`

```
docker volume create pavan
```
`Logical filesystem/partition on Host`

```
docker volume inspect pavan
```
`To get details of specific volume`

```
docker volume rm pavan
```
`Delete pavan volume created earlier`

```
docker run -d —mount source=pavan,target=/app <image-name>
```
`Attach mount to a docker container`

---
## Docker Bind Mounts

Bind mounts also aims to solve the same problem but in a complete different way.

Using this way, user can mount a directory from the host file system into a container. Bind mounts have the same behavior as volumes, but
are specified using a host path instead of a volume name. 

```
docker run -it -v <host_path>:<container_path> <image_name> /bin/bash
```

---
## Key Differences between Volumes and Bind Directory on a host as a Mount

- Volumes are managed, created, mounted and deleted using the Docker API. However, Volumes are more flexible than bind mounts, as 
they can be managed and backed up separately from the host file system, and can be moved between containers and hosts.

- In a nutshell, Bind Directory on a host as a Mount are appropriate for simple use cases where you need to mount a directory from the host file system into
a container, while volumes are better suited for more complex use cases where you need more control over the data being persisted
in the container.
