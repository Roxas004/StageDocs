# Docker

## 1. Introduction

Docker is an open-source platform that automates the deployment of applications within **software containers**.  
These containers bundle **everything an application needs to run** (code, dependencies, configuration, runtime) and ensure **consistent execution on any system** equipped with Docker.

---

## 2. Why Docker?

### Key Advantages

- **Portability**: A container can run identically in any environment (development, CI, production).
- **Isolation**: Dependencies and processes are compartmentalized within each container.
- **Performance**: Containers are lighter than virtual machines, thanks to sharing the system kernel.
- **DevOps Productivity**: Docker integrates seamlessly into modern CI/CD pipelines.
- **Scalability**: Starting multiple instances of the same application is quick and trivial.

---

## 3. Fundamental Concepts

### Docker Image

A **Docker image** is an immutable (read-only) template containing:
- The application's source code,
- System and software dependencies,
- The configuration required for execution.

> An image is built from a `Dockerfile`.

---

### Docker Container

A **Docker container** is an **executable instance** of an image:
- It is isolated from the host system.
- It has a read-write file system (non-persistent unless volumes are used).
- It is ephemeral by nature (but can be restarted, kept, or deleted).

---

### Dockerfile

The `Dockerfile` is a configuration file describing **the steps to build** an image.

Example :
```dockerfile
FROM node:18-alpine
WORKDIR /usr/src/app
COPY . .
RUN npm install
CMD ["node", "index.js"]
```

---

### Docker Compose

Docker Compose is a tool for **defining and running multi-container applications** using a [docker-compose.yml](../docker-compose.yml) file.

Example :
```yaml
version: '3.9'
services:
  web:
    build: .
    ports:
      - "3000:3000"
    depends_on:
      - db
  db:
    image: postgres:15
    environment:
      POSTGRES_PASSWORD: example
```

---

### Docker Hub & Registries

**Docker Hub** is a **public Docker image registry** (official).  
It is the default source for `docker pull` commands.

You can :
- Use official images (e.g., `nginx`, `mysql`, `python`).
- Push your own images (public or private).
- Host a private registry (e.g., GitLab Registry, AWS ECR, etc.).

---

### Docker Engine

The Docker engine is composed of three main elements :
- **`dockerd` (daemon)**: Background service managing containers.
- **REST API**: Interface for communicating with the daemon.
- **CLI `docker`**: Command-line tool for manipulating Docker (`run`, `build`, `push`, etc.).

---

## 4. Commands

### Basic Commands

| Action                                       | Command                          |
|----------------------------------------------|----------------------------------|
| List active containers                       | `docker ps`                      |
| View all images                              | `docker images`                  |
| Clean up dangling images                     | `docker image prune -a`          |
| Enter a container                            | `docker exec -it <id> /bash/sh`  |
| Follow logs                                  | `docker-compose logs -f`         |
| Start all defined services in detached mode  | `docker-compose up -d --build`   |
| Stop and remove containers                   | `docker-compose down`            |
| Stop containers without removing them        | `docker-compose stop`            |
| Restart stopped containers                   | `docker-compose start`           |

---

### Managing Docker Commands with Makefile

To simplify the use of Docker in this project, common Docker commands have been integrated into a [Makefile](../Makefile). This provides mnemonic shortcuts and ensures consistency among developers.

Instead of typing long docker ... commands manually, you will use shorter, more descriptive make commands.

To see the list of all Docker commands managed by the Makefile, their descriptions, and configurable variables, run:

```bash
make docker   # List all Docker commands and variables
```

---

## 5. Additional Resources

- [Official Docker Documentation](https://docs.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)
- [Dockerfile Best Practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
- [DockerHub](https://hub.docker.com/)

