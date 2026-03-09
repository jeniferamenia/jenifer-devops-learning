# Docker Fundamentals – Notes

These notes document the key Docker concepts learned while building containerized applications and multi-container services using Docker and Docker Compose.

---

# 1. What is Docker

Docker is a **containerization platform** used to package applications with their dependencies so they run consistently across environments.

Instead of running software directly on the host machine, applications run inside **containers**, which isolate the application and its dependencies.

Benefits:

- Consistent environments across development and production
- Lightweight compared to virtual machines
- Fast startup times
- Simplified deployment

---

# 2. Containers vs Virtual Machines

| Containers | Virtual Machines |
|---|---|
| Share host OS kernel | Each VM has its own OS |
| Lightweight | Heavy |
| Fast startup | Slow startup |
| Efficient resource usage | Higher resource usage |

Containers run **on top of the host OS**, while virtual machines require a **hypervisor and full OS installation**.

---

# 3. Docker Architecture

Key components:

**Docker Client**  
The CLI used to run Docker commands.

**Docker Daemon**  
The background service that builds, runs, and manages containers.

**Docker Images**  
Read-only templates used to create containers.

**Docker Containers**  
Running instances of Docker images.

**Docker Registry**  
A repository used to store Docker images (e.g., Docker Hub).

---

# 4. Docker Images

A **Docker image** is a blueprint used to create containers.

Images contain:

- Application code
- Runtime
- Libraries
- Dependencies
- Environment configuration

Images are built from a **Dockerfile**.

Example:

```bash
docker build -t flask-app .
```

---

# 5. Docker Containers

A **container** is a running instance of a Docker image.

Containers are:

- Isolated
- Portable
- Lightweight

Example:

```bash
docker run -p 5000:5000 flask-app
```

This maps:

Host Port → Container Port

---

# 6. Dockerfile

A **Dockerfile** contains instructions used to build an image.

Common instructions:

### FROM
Defines the base image.

```dockerfile
FROM python:3.8-slim
```

### WORKDIR
Sets the working directory inside the container.

```dockerfile
WORKDIR /app
```

### COPY
Copies files from the host into the container.

```dockerfile
COPY . .
```

### RUN
Executes commands during the build process.

```dockerfile
RUN pip install flask redis
```

### EXPOSE
Documents which ports the container will use.

```dockerfile
EXPOSE 5000
```

### CMD
Defines the command executed when the container starts.

```dockerfile
CMD ["python", "app.py"]
```

---

# 7. Docker Compose

Docker Compose allows multiple containers to run as a **single application stack**.

Configuration is defined in a `docker-compose.yml` file.

Example services:

- Web application
- Database
- Cache service

Example:

```yaml
version: '3.8'

services:
  web:
    build: .
    ports:
      - "5000:5000"

  redis:
    image: redis:latest
```

Command to start services:

```bash
docker compose up
```

Stop services:

```bash
docker compose down
```

---

# 8. Container Networking

Docker Compose automatically creates a **shared network**.

Containers communicate using **service names**.

Example:

```
redis:6379
```

The Flask container can connect to Redis using the service name `redis`.

Docker internally resolves this hostname.

---

# 9. Docker Volumes (Persistent Storage)

By default, container data is **ephemeral**.

If a container is removed, its data is lost.

Volumes allow data to persist outside containers.

Example:

```yaml
volumes:
  redis-data:
```

Mounting a volume:

```yaml
services:
  redis:
    image: redis
    volumes:
      - redis-data:/data
```

This ensures Redis data persists even if containers restart.

---

# 10. Environment Variables

Environment variables allow configuration without modifying application code.

Example in Docker Compose:

```yaml
environment:
  REDIS_HOST: redis
  REDIS_PORT: 6379
```

Inside Python:

```python
os.getenv("REDIS_HOST")
```

Benefits:

- Flexible configuration
- Environment-specific settings
- Improved security

---

# 11. Scaling Containers

Docker Compose allows horizontal scaling.

Example:

```bash
docker compose up --scale web=3
```

This creates multiple containers for the same service:

```
web-1
web-2
web-3
```

Scaling improves:

- Performance
- Availability
- Fault tolerance

---

# 12. Reverse Proxy and Load Balancing

When multiple containers run, requests must be distributed between them.

This is handled by a **reverse proxy**.

Example: **NGINX**

Architecture:

User Request  
↓  
NGINX Reverse Proxy  
↓  
Multiple Flask Containers  
↓  
Redis Database

NGINX forwards incoming traffic to available containers.

---

# 13. Debugging Docker

Useful commands:

List running containers

```bash
docker ps
```

View container logs

```bash
docker logs container_id
```

Execute commands inside a container

```bash
docker exec -it container_id bash
```

Remove unused resources

```bash
docker system prune
```

---

# 14. DevOps Concepts Demonstrated

This Docker learning project demonstrates:

- Containerization
- Multi-service architecture
- Service networking
- Persistent data volumes
- Environment configuration
- Horizontal scaling
- Reverse proxy load balancing

These are core concepts used in modern DevOps and cloud-native infrastructure.