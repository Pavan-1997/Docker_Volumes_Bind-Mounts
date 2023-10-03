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

Below are a few more commands related to docker volumes

	1. docker volume ls 
	(To view all volumes)
	2. docker volume create pavan
	(Logical filesystem/partition on Host)
	3. docker volume inspect pavan
	(To get details of specific volume)
	4. docker volume rm pavan
	(Delete pavan volume created earlier)
	5. docker run -d —mount source=pavan,target=/app <image-name>
(Attach mount to a docker container)

This command will mount the volume <volume_name> to the /data directory in the container. Any data written to the /data directory
inside the container will be persisted in the volume on the host file system.
