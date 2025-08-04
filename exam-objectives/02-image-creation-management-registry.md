# ✅ Exam Objective 2: Image Creation, Management, and Registry (20%)

This section focuses on building images using best practices, managing image layers, using registries, and scanning for vulnerabilities.

---

## 🐳 Building Docker Images

### Create a Dockerfile

```dockerfile
FROM python:3.12-slim
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
CMD ["python", "main.py"]
```

### Build the Image

```bash
docker build -t myapp:latest .
```

### Best Practices

- Use official base images
- Minimize image size (multi-stage builds, `.dockerignore`)
- Pin versions (e.g. `node:20-alpine`, not `node:latest`)

---

## 📦 Multi-Stage Builds

Used to separate build-time dependencies from runtime environment.

```dockerfile
# Build stage
FROM golang:1.21 AS builder
WORKDIR /app
COPY . .
RUN go build -o app

# Runtime stage
FROM alpine
COPY --from=builder /app/app /app
ENTRYPOINT ["/app"]
```

---

## 🙈 .dockerignore

Exclude files from the build context to speed up builds and reduce image size.

Example `.dockerignore`:

```
.git
node_modules
*.log
Dockerfile*
```

---

## 🏷 Tagging & Pushing Images

### Tag an Image

```bash
docker tag myapp:latest myusername/myapp:1.0
```

### Push to Docker Hub

```bash
docker push myusername/myapp:1.0
```

### Pull from Docker Hub

```bash
docker pull myusername/myapp:1.0
```

> ⚠️ Make sure you're logged in: `docker login`

---

## 🏠 Private & Self-Hosted Registries

Run a local registry:

```bash
docker run -d -p 5000:5000 --name registry registry:2
```

Tag and push to it:

```bash
docker tag myapp localhost:5000/myapp
docker push localhost:5000/myapp
```

> You may need to configure the daemon to allow insecure registries.

---

## 🔍 Inspecting Image Layers

### View Image History

```bash
docker image history myapp
```

### Inspect Image Metadata

```bash
docker image inspect myapp
```

---

## 🔐 Image Scanning

### Docker Scan (powered by Snyk)

```bash
docker scan myapp
```

Requires Docker Desktop or `docker-scan-plugin`.

---

## 🧪 Practice Prompts

- Write a Dockerfile for a Python/Node app using best practices
- Use `.dockerignore` to exclude dev files
- Create a multi-stage build for a Go or Java app
- Push an image to Docker Hub or a local registry
- Inspect image layers and understand what each one does
- Run a vulnerability scan on your image

---

## 📌 Summary

| Task                          | Command |
|-------------------------------|---------|
| Build image                   | `docker build -t myapp .` |
| Tag image                     | `docker tag` |
| Push/pull image               | `docker push`, `docker pull` |
| View image layers             | `docker image history` |
| Inspect metadata              | `docker image inspect` |
| Scan image                    | `docker scan` |

---

## 📖 References

- [Dockerfile Reference](https://docs.docker.com/engine/reference/builder/)
- [Image Management CLI](https://docs.docker.com/engine/reference/commandline/image/)
- [Docker Hub](https://hub.docker.com/)
- [Docker Scan Docs](https://docs.docker.com/engine/scan/)
