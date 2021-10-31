# Docker

Summary of Docker's getting started.

- [CLI commands](#cli-commands)

## What is container?

A container is simply another process on your machine that has been isolated from all other processes on the host machine.

## What is container image?

When running a container, it uses an isolated filesystem. This custom filesystem is provided by a container image.

## Dockerfile

A Dockerfile is simply a text-based script of instructions that is used to create a container image.

## Volumes

Volumes provide the ability to connect specific filesystem paths of the container back to the host machine.

### Named Volumes

Named volumes are great if we simply want to store data, as we don't have to worry about _where_ the data is stored.

### Bind Mounts

With bind mounts, we control the exact mountpoint on the host. We can use this to persist data, but is often used to provide additional data into containers. When working on an application, we can use a bind mount to mount our source code into the container to let it see code changes, respond, and let us see the changes right away.

## CLI commands

### List images in local

```zsh
docker image list
```

### Build

```zsh
docker build -t <image-name> <Dockerfile-directory>
```

- `-t`: tag the image

### Start

```zsh
docker run -dp <host-port>:<container-port> <image-name>
```

- `-d`: detached mode (in the background)
- `-p`: map the host port to the container port
- `-dp`: combine `-d` and `-p`

#### Start with a specific volume

```zsh
docker run -dp <host-port>:<container-port> -v <volume-name>:<mount-directory>
```

#### example

```zsh
docker run -dp 3000:3000 -v todo-db:/etc/todos getting-started
```

### Get the ID of the container

```zsh
docker ps
```

### Stop

```zsh
docker stop <the-container-id>
```

### Remove

```zsh
docker rm <the-container-id>
```

> You can only remove the stopped containers.

#### Stop and remove (force remove)

```zsh
docker rm -f <the-container-id>
```

### Create a volume

```zsh
docker volume create <volume-name>
```

### Inspect a volume

```zsh
docker volume inspect <volume-name>
```
