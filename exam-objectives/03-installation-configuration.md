# ✅ Exam Objective 3: Installation and Configuration (15%)

This section covers how to install Docker, configure the daemon, manage startup behavior, logging, and differentiate between editions and deployment contexts.

---

## 🧰 Installing Docker

### On Linux (Ubuntu Example)

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

> Alternative: Use package manager for finer control

### On Windows / macOS

- Use **Docker Desktop** (includes Docker Engine, CLI, Docker Compose, and Kubernetes)
- Requires WSL 2 on Windows

---

## 🧠 Understand Editions

| Edition | Use Case |
|--------|----------|
| **Community Edition (CE)** | Free for individuals and small teams |
| **Enterprise Edition (EE)** | Paid features, support, and certified plugins |
| **Mirantis** | Maintains Docker Enterprise after Docker Inc. sold the product line |

---

## ⚙️ Docker Daemon Configuration

Located at:

```bash
/etc/docker/daemon.json
```

Example:

```json
{
  "log-driver": "json-file",
  "storage-driver": "overlay2",
  "insecure-registries": ["localhost:5000"]
}
```

Restart Docker after changes:

```bash
sudo systemctl restart docker
```

---

## 🔌 Start Docker on Boot

Enable the service:

```bash
sudo systemctl enable docker
```

Check status:

```bash
sudo systemctl status docker
```

---

## 📝 Logging Drivers

Set via `--log-driver` flag or in `daemon.json`.

Common logging drivers:

- `json-file` (default)
- `syslog`
- `journald`
- `awslogs`
- `fluentd`

Example:

```bash
docker run --log-driver syslog nginx
```

---

## 🔐 Configure Docker Engine with TLS

To enable secure client-server communication:

1. Generate TLS certificates (CA, server cert, client cert)
2. Add the following to `daemon.json`:

```json
{
  "tls": true,
  "tlsverify": true,
  "tlscacert": "/etc/docker/ca.pem",
  "tlscert": "/etc/docker/server-cert.pem",
  "tlskey": "/etc/docker/server-key.pem",
  "hosts": ["tcp://0.0.0.0:2376", "unix:///var/run/docker.sock"]
}
```

3. Restart Docker and test TLS with `docker --tls ...`

---

## 📦 Docker Contexts

Switch between Docker endpoints (e.g., local vs remote):

```bash
docker context ls
docker context create my-remote \
  --docker "host=ssh://user@remote-host"
docker context use my-remote
```

Useful when managing multiple environments.

---

## 🧪 Practice Prompts

- Install Docker on a fresh Linux VM
- Configure Docker to start at boot and use `overlay2`
- Change the logging driver and verify container logs
- Set up a remote context and deploy a container over SSH
- Edit `daemon.json` to allow an insecure registry and restart Docker

---

## 📌 Summary

| Task                              | Command |
|-----------------------------------|---------|
| Install Docker (quick script)     | `curl https://get.docker.com | sh` |
| Start Docker at boot              | `systemctl enable docker` |
| Set daemon config                 | `/etc/docker/daemon.json` |
| Restart Docker                    | `systemctl restart docker` |
| Change logging driver             | `--log-driver`, or in config |
| Manage contexts                   | `docker context` |

---

## 📖 References

- [Install Docker Engine](https://docs.docker.com/engine/install/)
- [Daemon CLI Reference](https://docs.docker.com/engine/reference/commandline/dockerd/)
- [Logging Drivers](https://docs.docker.com/config/containers/logging/configure/)
- [Docker Contexts](https://docs.docker.com/engine/context/working-with-contexts/)
