# Docker Cookbook


###  Get Docker Version
```bash
  docker version
```

### Docker Images 

1. Search Images (available)

```shell
  docker search [OPTIONS] <keyword>
```

```bash
  docker search --limit 5 alpine 
```

2. Pull Image

```bash 
  docker image pull [OPTIONS] <name>[:TAG:@DIGEST]
```

```bash
  docker image pull ubuntu
```

3. List Images (available on the system)

```bash
  docker image ls
```

## Docker Containers

All the container commands are grouped under `docker container`

1. Start Container (creates & starts the container)

```bash
  docker container run -i -t --name mycontainer ubuntu /bin/bash
```

* `-i` / `--interactive` - starts the container in interactive mode
* `-t` / `-tty` - allocates a `pseudo-tty` and attaches it to the standard input. 
* `-d` - start container in background

The above command starts a container from `ubuntu:latest` image, attaches `pseudo-tty`, names the container `mycontainer` and executes `/bin/bash` command.

*In case the image is not avaiable locally, then it is first fetched from the registry and then run.*

2. Exit Container 
Press `Ctrl+D` or type `exit`.

```bash
  exit
```

4. Create Container 

```bash
  ID=$(docker container create -d -i -t ubuntu /bin/bash)
  docker container start -a -i $ID
```

The container is created with `docker container create` command, and then we later start and attach with it using `docker container start -a -i`  

5. Remove the container, after it exists

```bash
  docker run --rm ubuntu pwd
```

*As soon as `pwd` command exits, the container will be removed.*

6. Listing Containers 

```bash
  docker container ls [OPTIONS]
```
 
```bash

  # List both running & stopped containers.
  docker container -a
  
  # List the last created container
  docker container ls -l
```

### Container Logs

```bash
  docker container logs [OPTIONS] <container-id>
```

```
  # Get logs with timestamp
  docker container logs -t $ID
```

### Stopping Containers

```bash
  docker container stop [OPTIONS] <container-id>
```

```bash
  ID=$(docker container run ubuntu /bin/bash)
  docker stop $ID
```

```bash
   # Stop all running containers
   docker container stop $(docker ps -q)
```

### Removing a Container

```bash
  docker container rm [OPTIONS] <container-id> [...CONTAINER-ID]
```

```bash
  ID = $(docker container create ubuntu /bin/bash)
  docker container stop $ID
  docker container rm $ID
```

- A runnning container must be stopped first before it is removed. In order to forcefully remove a container (*without stopping*) the `-f` option with `rm` command should be used. 

```
  # Remove all stopped containers at once.
  docker container prune
  
  # Remove stopped containers w/o prompt
  docker container prune -f
```

### Container Restart Policy (in case of container failure/ reboot)

- requires Docker > 1.2
- automated container restart on Docker Host Reboot / Container failures.
- `--restart` option of the Docker `run` command.

```bash
  docker container run --restart=POLICY [OPTIONS] IMAGE[:TAG]
```

```bash
  docker container run --restart=always -d -i -t ubuntu /bin/bash
```

There are three restart policies to choose from `always`, `no`, `on-failure`.

```bash
  # put a restart count on-failure policy
  docker container run --restart=on-failure:3 -d -i -t ubuntu /bin/bash
```

# Privileged access inside a container

Linux divides privileges associated with superusers `sudoers` into distinct units, known as `capabilities`.

```bash
  man capabilities
```

These privileges can be independently enabled & disabled. For example `net_bind_services` capability allows non-user process to bind the port below 1024.

By default, docker start containers with limited capabilities. W/ privileged access inside the container, we alllow more capabilities to perform abilities that are normally done by the root user. 

```bash
  docker container run --privileged [OPTIONS] <image> [COMMAND] [...args]
```

```bash
  # sudo capabilities *security risk associated*
  docker container run --privileged -i -t ubuntu /bin/bash
  
  # prevent CHOWN inside the container
  docker container run --cap-drop=CHOWN -i -t ubuntu /bin/bash
```

# Provide access to the HOST Device

```bash
  docker container run --device=<host-device>:<container-device>:<permissions> [OPTIONS] <image> [COMMAND] [...ARG]
  
```

```bash
  docker container run --device=/dev/sdc:/dev/xvdc -i -t ubuntu /bin/bash
```

# Injecting new Process into running Container

- Utilites such as `nsenter` github.com/jpetazzo/nsenter allows us to inspect the state of a running container. 
- In docker 1.3, the `exec` command was added, which allows injecting process inside a running container.

```bash
  docker exec [OPTIONS] <container> <command> <...args>
```

```bash 
  ID = $(docker container run -d redis)
  docker container exec -it $ID /bin/bash
```

# Inspecting Container
It provides meta information about a container.

```bash
  docker container inspect [OPTIONS] <container>
```

```
  ID = $(docker container run -i -t ubuntu /bin/bash)
  docker container inspect $ID
```

- the metadata is presented in JSON format.
- using tools such as `jq`, this JSON data can be further processed.

# Labelling & Filtering Containers
Docker 1.6 allows labelling of containers and images, by attaching key-value pairs as metadata.

- Labels attached to images gets applied to containers that are started using those images. 
- Labels can also be attached to container while starting them. 
- `-l`/`--label` option of the `docker container run` command is used to attach labels to the container.

```bash
  docker container run --label com.example.container=docker-cookbook label-demo date
```

- `-f`/ `--filter` option along with `docker container ls` command is used to filter out containers with given labels. 

```bash
  docker container ls -a --filter=com.example.container=docker-cookbook
```