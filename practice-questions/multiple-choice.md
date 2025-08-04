# 🧪 Multiple Choice Practice – Docker Certified Associate

Use the questions below to test your knowledge before checking the answers. Each question corresponds to a DCA exam domain. Answers are provided in a separate document.

---

## ✅ 1. Orchestration

**Q1.** What command initializes a Docker Swarm cluster?

A. `docker swarm create`  
B. `docker init swarm`  
C. `docker swarm init`  
D. `docker init`

---

**Q2.** Which command is used to deploy a stack from a Compose file in a Swarm?

A. `docker deploy`  
B. `docker compose up`  
C. `docker service deploy`  
D. `docker stack deploy -c <file> <name>`

---

## ✅ 2. Image Creation, Management, and Registry

**Q3.** What file is used to exclude files and folders from a Docker image build context?

A. `Dockerfile`  
B. `.dockeringore`  
C. `.dockerignore`  
D. `docker.exclude`

---

**Q4.** Which Dockerfile instruction reduces image size by combining steps?

A. `RUN`  
B. `COPY`  
C. `FROM`  
D. `CMD`

---

## ✅ 3. Installation and Configuration

**Q5.** Where is the Docker daemon configuration file typically located on Linux?

A. `/etc/docker/config.json`  
B. `/var/lib/docker/config.json`  
C. `/etc/docker/daemon.json`  
D. `/usr/docker/daemon.conf`

---

**Q6.** Which command sets Docker to start at boot?

A. `docker enable`  
B. `docker start`  
C. `systemctl enable docker`  
D. `docker boot-config`

---

## ✅ 4. Networking

**Q7.** Which command creates a user-defined bridge network?

A. `docker create network mynet`  
B. `docker network add mynet`  
C. `docker network create mynet`  
D. `docker net new mynet`

---

**Q8.** What is the main benefit of user-defined bridge networks over the default bridge?

A. Better CPU usage  
B. Automatic DNS resolution by container name  
C. Lower memory usage  
D. Faster startup

---

## ✅ 5. Security

**Q9.** What command enables image signature verification in Docker?

A. `docker --verify-signatures`  
B. `docker trust enable`  
C. `export DOCKER_CONTENT_TRUST=1`  
D. `docker enable content-trust`

---

**Q10.** Which tool is recommended to audit Docker host security?

A. `docker secure`  
B. `docker scan`  
C. `docker-bench-security`  
D. `dockersec`  

---

## ✅ 6. Storage and Volumes

**Q11.** Which command backs up a named volume using a tarball?

A. `docker volume export`  
B. `tar -czf` from a container mounting the volume  
C. `docker cp`  
D. `docker volume backup`

---

**Q12.** Which statement is true about bind mounts?

A. They are stored in Docker-managed paths.  
B. They persist beyond container deletion.  
C. They are used only in Swarm.  
D. They require a named volume.

---

## 📖 Notes

- For answer explanations, see [`answers.md`](./answers.md).
- Randomize questions for mock exam simulations.
- Try answering from memory before checking the official docs.
