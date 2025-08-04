# ✅ Exam Objective 1: Orchestration (25%)

Swarm mode is the **core orchestration feature** Docker expects you to know for the DCA exam. This domain covers deploying, managing, and scaling services using Swarm.

---

## 🐝 Swarm Mode Basics

### Initialize a Swarm Cluster

```bash
docker swarm init
```

- Creates the first **manager** node.
- Returns a join token for adding workers.

### Join Additional Nodes

```bash
docker swarm join --token <TOKEN> <MANAGER-IP>:2377
```

---

## 🧠 Node Management

### Promote/Demote Nodes

```bash
docker node promote <NODE-ID>
docker node demote <NODE-ID>
```

- Use `docker node ls` to list nodes
- Managers can vote on updates and manage the cluster

---

## ⚙️ Deploying Services

### Create a Service

```bash
docker service create --name web --replicas 3 -p 80:80 nginx
```

### List & Inspect Services

```bash
docker service ls
docker service ps <SERVICE-NAME>
```

---

## 🔁 Scaling and Updating Services

### Scale a Service

```bash
docker service scale web=5
```

### Perform Rolling Update

```bash
docker service update --image nginx:1.25 web
```

- Docker updates containers one at a time (can customize update policy)

### Roll Back a Service

```bash
docker service rollback web
```

---

## 📍 Placement Constraints & Preferences

### Use Constraints

```bash
docker service create --constraint 'node.labels.env==prod' ...
```

### Use Preferences

```bash
docker service create --placement-pref 'spread=node.labels.zone' ...
```

---

## 🔒 Secrets & Configs

### Create & Use a Secret

```bash
echo "my-secret" | docker secret create db_pass -
docker service create --name db \
  --secret db_pass \
  mysql
```

- Secrets are mounted as files in `/run/secrets`

### Add Configs

```bash
echo "config content" | docker config create my_config -
```

---

## 🌐 Overlay Networks

### Create Overlay Network

```bash
docker network create -d overlay my_overlay
```

- Used to connect services across nodes

### Deploy Service Using Overlay Network

```bash
docker service create --name app \
  --network my_overlay \
  nginx
```

---

## 🧾 Troubleshooting Services

### Check Service Logs

```bash
docker service logs web
```

### View Task Details

```bash
docker service ps web
docker inspect <TASK-ID>
```

---

## 📦 Using Docker Stacks

Stacks let you deploy multi-service applications from a `docker-compose.yml` file.

### Example `stack.yml`

```yaml
version: "3"
services:
  web:
    image: nginx
    ports:
      - "80:80"
```

### Deploy the Stack

```bash
docker stack deploy -c stack.yml mystack
```

### Remove the Stack

```bash
docker stack rm mystack
```

---

## 🧪 Practice Prompts

- Create a Swarm cluster with 1 manager and 2 workers.
- Deploy a replicated service and update it to a new version.
- Practice using placement constraints by labeling nodes.
- Configure and deploy a service with a secret.
- Use `docker stack deploy` to run a multi-service app.

---

## 📌 Summary

| Topic                      | Key Command |
|---------------------------|-------------|
| Init Swarm                | `docker swarm init` |
| Join Node                 | `docker swarm join` |
| Create Service            | `docker service create` |
| Scale/Update Service      | `docker service scale`, `update` |
| Secrets                   | `docker secret create` |
| Overlay Network           | `docker network create -d overlay` |
| Stack Deploy              | `docker stack deploy` |

---

## 📖 References

- [Swarm Mode Overview](https://docs.docker.com/engine/swarm/)
- [Docker Service CLI](https://docs.docker.com/engine/reference/commandline/service/)
- [Docker Stacks and Compose Files](https://docs.docker.com/compose/)
