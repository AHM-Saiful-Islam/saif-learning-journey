
# 🐳 Docker Documentation for Projects

This guide provides a beginner-to-intermediate overview of using Docker in backend development. It covers setup, image creation, container management, and Docker Compose.

---

## 📦 What is Docker?

Docker is an open-source platform for developing, shipping, and running applications in containers. Containers allow developers to package applications with all dependencies and run them in any environment.

---

## 🛠️ Prerequisites

- Install [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- (Optional) Install [Docker Compose](https://docs.docker.com/compose/install/) – included in Docker Desktop
- Basic understanding of terminal and backend development

---

## 🐳 Basic Docker Commands

| Action | Command |
|--------|---------|
| Check Docker version | `docker --version` |
| Pull an image | `docker pull <image-name>` |
| List images | `docker images` |
| Run a container | `docker run -d -p 8000:8000 <image-name>` |
| List running containers | `docker ps` |
| Stop a container | `docker stop <container-id>` |
| Remove a container | `docker rm <container-id>` |
| Remove an image | `docker rmi <image-name>` |

---

## 📄 Dockerfile Example (Python Flask App)

```Dockerfile
# Use an official Python runtime as a parent image
FROM python:3.10-slim

# Set working directory
WORKDIR /app

# Copy project files
COPY . .

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Expose the app port
EXPOSE 5000

# Run the app
CMD ["python", "app.py"]
```

---

## ⚙️ Build & Run Docker Image

```bash
# Build the Docker image
docker build -t my-backend-app .

# Run the container
docker run -d -p 5000:5000 my-backend-app
```

---

## 🧩 Docker Compose Example

Create a `docker-compose.yml` file for multi-container apps:

```yaml
version: '3.9'
services:
  web:
    build: .
    ports:
      - "5000:5000"
    volumes:
      - .:/app
    environment:
      - FLASK_ENV=development
  db:
    image: postgres:14
    environment:
      POSTGRES_DB: mydb
      POSTGRES_USER: user
      POSTGRES_PASSWORD: password
    ports:
      - "5432:5432"
```

Start all services:

```bash
docker-compose up --build
```

Stop all services:

```bash
docker-compose down
```

---

## ✅ Best Practices

- Use `.dockerignore` to exclude unnecessary files
- Use multi-stage builds to reduce image size
- Tag images with versions: `myapp:1.0.0`
- Keep secrets and environment variables out of the image
- Use `volumes` for persistent data

---

## 📚 Resources

- [Docker Official Documentation](https://docs.docker.com/)
- [Awesome Docker](https://github.com/veggiemonk/awesome-docker)
- [Docker Cheat Sheet](https://github.com/wsargent/docker-cheat-sheet)

---

> 📝 **Tip**: Add `Dockerfile`, `.dockerignore`, and `docker-compose.yml` to your project root for easy integration with CI/CD workflows.
