# ✅ Exam Objective 5: Security (15%)

This section focuses on Docker’s security features: isolation, capabilities, image scanning, secrets management, and daemon protection.

---

## 🔒 Docker Security Model

Docker uses several Linux features to isolate containers:

| Feature        | Purpose                        |
|----------------|--------------------------------|
| **Namespaces** | Isolate container resources (PID, NET, UTS, etc.) |
| **Cgroups**    | Limit CPU, memory, disk I/O usage |
| **Capabilities** | Drop unneeded root powers |
| **Seccomp**    | Filter syscalls |

Containers are not VMs — they share the host kernel.

---

## 👤 Run Containers as Non-Root

Avoid using `USER root` in Dockerfiles.

```dockerfile
RUN adduser --disabled-password appuser
USER appuser
```

Or override at runtime:

```bash
docker run -u 1001 myapp
```

---

## 🔍 Scanning for Vulnerabilities

### Docker Scan (Snyk)

```bash
docker scan myimage
```

Requires Docker Desktop or `docker-scan-plugin`.

### Alternative: Use `trivy`

```bash
trivy image myimage
```

---

## 🧢 Limiting Capabilities

By default, containers run with a limited set of Linux capabilities. You can remove or add specific ones.

### Drop All Capabilities

```bash
docker run --cap-drop=ALL nginx
```

### Add a Specific Capability

```bash
docker run --cap-add=NET_ADMIN alpine
```

---

## 🧰 Docker Bench for Security

Audit your Docker host:

```bash
docker run -it --net host --pid host \
  --cap-add audit_control \
  --label docker_bench_security \
  --volume /var/lib:/var/lib \
  --volume /var/run/docker.sock:/var/run/docker.sock \
  --volume /etc:/etc \
  docker/docker-bench-security
```

Outputs a full security report.

---

## 🔑 Secrets Management

Only available in Swarm mode.

### Create a Secret

```bash
echo "mypassword" | docker secret create db_pass -
```

### Use Secret in a Service

```bash
docker service create --name db \
  --secret db_pass \
  mysql
```

Mounted as `/run/secrets/db_pass` inside the container.

---

## 🛡 Enable Content Trust

Verify image publisher and integrity.

```bash
export DOCKER_CONTENT_TRUST=1
docker pull myimage
```

Requires signed images (not all Docker Hub images support this).

---

## 🔐 Secure the Docker Daemon

### Enable TLS

Use `daemon.json` to set:

```json
{
  "tls": true,
  "tlsverify": true,
  "tlscacert": "/etc/docker/ca.pem",
  "tlscert": "/etc/docker/server-cert.pem",
  "tlskey": "/etc/docker/server-key.pem"
}
```

Access with:

```bash
docker --tlsverify --tlscacert=... --tlscert=... --tlskey=... -H <host>:2376 info
```

---

## 🧪 Practice Prompts

- Build an image that runs as a non-root user
- Drop all capabilities and verify limited access
- Scan a custom image for vulnerabilities
- Run Docker Bench and review findings
- Create and use a secret in Swarm mode
- Configure `DOCKER_CONTENT_TRUST` and try pulling a signed/unsigned image

---

## 📌 Summary

| Task                            | Command |
|----------------------------------|---------|
| Run as non-root                  | `USER` in Dockerfile or `-u` flag |
| Drop/add capabilities            | `--cap-drop`, `--cap-add` |
| Scan image                       | `docker scan`, `trivy` |
| Create and mount secret (Swarm) | `docker secret create`, `--secret` |
| Audit with Docker Bench         | `docker/docker-bench-security` |
| Enable content trust             | `export DOCKER_CONTENT_TRUST=1` |

---

## 📖 References

- [Docker Security Docs](https://docs.docker.com/engine/security/)
- [Docker Bench for Security](https://github.com/docker/docker-bench-security)
- [Docker Content Trust](https://docs.docker.com/engine/security/trust/)
- [Linux Capabilities](https://man7.org/linux/man-pages/man7/capabilities.7.html)
