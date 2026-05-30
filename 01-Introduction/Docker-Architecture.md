# Docker Architecture

## What I Learned

While learning Docker, I initially thought that the `docker` command itself was responsible for creating and managing containers.

After exploring Docker Architecture, I understood that the Docker CLI is only a client. It doesn't perform any container operations directly.

For example, when I execute:

```bash
docker run nginx
```

the request is sent to the Docker Daemon (`dockerd`), which performs the actual work such as downloading images, creating containers, starting containers, and managing Docker resources.

---

## Architecture Overview

```text
User
  |
  v
Docker CLI (Client)
  |
  v
Docker Daemon (dockerd)
  |
  +---- Images
  |
  +---- Containers
  |
  +---- Networks
  |
  +---- Volumes
```

---

## Components

### Docker Client

The Docker Client is the command-line interface that I use to interact with Docker.

Examples:

```bash
docker run nginx
docker ps
docker images
docker pull ubuntu
```

The client only sends requests. It does not create containers by itself.

---

### Docker Daemon

The Docker Daemon (`dockerd`) is the core component of Docker.

It is responsible for:

* Pulling images
* Building images
* Creating containers
* Starting and stopping containers
* Managing networks
* Managing volumes

Whenever I run a Docker command, the daemon processes the request.

---

### Docker Images

Images are templates used to create containers.

Examples:

```text
ubuntu
nginx
mysql
node
```

An image contains everything required to run an application.

To view available images:

```bash
docker images
```

---

### Docker Containers

Containers are running instances of images.

Example:

```bash
docker run nginx
```

This creates and starts a container using the nginx image.

To view running containers:

```bash
docker ps
```

---

### Docker Registry

A registry is a storage location for Docker images.

By default, Docker uses Docker Hub.

Example:

```bash
docker pull ubuntu
```

If the image is not available locally, Docker downloads it from the registry.

---

## Commands Practiced

```bash
docker images
docker ps
docker pull ubuntu
docker run nginx
```

---

## Observations

* Docker CLI and Docker Daemon are separate components.
* The Docker Daemon performs all Docker operations.
* Images are used to create containers.
* Containers are running instances of images.
* Docker automatically downloads an image if it is not available locally.
* Docker Hub acts as the default public registry.

---

## Easy Way to Remember

I compare Docker Architecture to a restaurant:

| Docker Component | Example        |
| ---------------- | -------------- |
| User             | Customer       |
| Docker Client    | Waiter         |
| Docker Daemon    | Kitchen        |
| Image            | Recipe         |
| Container        | Prepared Food  |
| Registry         | Food Warehouse |

The waiter takes the order but doesn't cook the food.

Similarly, the Docker Client accepts commands but the Docker Daemon performs the actual work.

---

## Key Takeaway

The most important thing I learned is that the Docker Client is only an interface.

The Docker Daemon is the component that manages images, containers, networks, and volumes behind the scenes.

