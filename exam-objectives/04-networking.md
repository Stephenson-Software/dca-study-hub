# ✅ Exam Objective 4: Networking (15%)

This domain covers Docker's networking model, container communication, network drivers, port publishing, and service discovery in Swarm.

---

## 🌉 Default Bridge Network

Every Docker installation comes with a default bridge network:

```bash
docker network ls
docker network inspect bridge
```

- Containers on the same bridge can communicate by IP
- Use `--link` for legacy name resolution (deprecated)

---

## 🔗 User-Defined Bridge Networks

Custom bridge networks support DNS-based name resolution.

```bash
docker network create my-net
docker run -d --name db --network my-net mysql
docker run -it --network my-net alpine ping db
```

---

## 🛠 Host and None Network Drivers

- `--network host`: container shares host’s network stack  
  - Useful for performance or specific protocols  
  - **Only works on Linux**

```bash
docker run --network host nginx
```

- `--network none`: disables networking entirely

---

## 🌐 Overlay Networks (Swarm)

Used to connect containers across nodes in a Swarm cluster.

### Create an Overlay Network

```bash
docker network create -d overlay my-overlay
```

### Use It in a Service

```bash
docker service create --name web \
  --network my-overlay \
  nginx
```

Overlay networks require Swarm mode.

---

## 🚪 Publishing Ports

Expose container ports to the host:

```bash
docker run -d -p 8080:80 nginx
```

- Format: `host_port:container_port`
- Use `docker ps` to confirm port bindings

---

## 🔍 DNS-Based Service Discovery (Swarm)

Swarm provides built-in DNS resolution by service name:

```bash
docker service create --name api --network app-net myapi
docker service create --name web --network app-net myweb
```

- `web` can resolve `api` by name
- Load balancing is built in (round robin)

---

## 🧪 Troubleshooting Networking

### Common Commands

```bash
docker network ls
docker network inspect <network>
docker exec <container> ping <other-container>
```

### Inspect Container Interfaces

```bash
docker exec -it <container> ip addr
docker exec -it <container> netstat -tuln
```

---

## 🧪 Practice Prompts

- Create and connect two containers with a user-defined bridge
- Publish a web app on port 8080 and access it via localhost
- Create a Swarm service using an overlay network
- Ping containers to verify connectivity
- Remove unused networks with `docker network prune`

---

## 📌 Summary

| Topic                      | Command |
|---------------------------|---------|
| List networks              | `docker network ls` |
| Create bridge/overlay      | `docker network create` |
| Inspect network            | `docker network inspect` |
| Connect container          | `--network my-net` |
| Publish port               | `-p host:container` |
| Test DNS in Swarm          | Ping service name from another service |

---

## 📖 References

- [Docker Networking Overview](https://docs.docker.com/network/)
- [Network Drivers](https://docs.docker.com/network/drivers/)
- [Service Discovery in Swarm](https://docs.docker.com/engine/swarm/networking/)
