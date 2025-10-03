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

**Q3.** How do you scale a service named "web" to 5 replicas in a Swarm?

A. `docker service scale web=5`  
B. `docker swarm scale web 5`  
C. `docker service update --replicas 5 web`  
D. Both A and C

---

**Q4.** What command is used to promote a worker node to a manager in a Swarm?

A. `docker node promote <node-id>`  
B. `docker swarm promote <node-id>`  
C. `docker node update --role manager <node-id>`  
D. `docker service promote <node-id>`

---

**Q5.** Which of the following is true about Docker Swarm services?

A. Services can only run on manager nodes  
B. Services automatically restart failed tasks  
C. Services require Kubernetes to operate  
D. Services cannot use overlay networks

---

## ✅ 2. Image Creation, Management, and Registry

**Q6.** What file is used to exclude files and folders from a Docker image build context?

A. `Dockerfile`  
B. `.dockeringore`  
C. `.dockerignore`  
D. `docker.exclude`

---

**Q7.** Which Dockerfile instruction reduces image size by combining steps?

A. `RUN`  
B. `COPY`  
C. `FROM`  
D. `CMD`

---

**Q8.** What is the correct order of Dockerfile instructions to optimize caching?

A. COPY code, RUN install dependencies, COPY dependencies file  
B. COPY dependencies file, RUN install dependencies, COPY code  
C. RUN install dependencies, COPY dependencies file, COPY code  
D. COPY code, COPY dependencies file, RUN install dependencies

---

**Q9.** Which command removes dangling images from your system?

A. `docker image prune`  
B. `docker rmi --dangling`  
C. `docker image clean`  
D. `docker remove images`

---

**Q10.** What is the primary benefit of multi-stage builds?

A. Faster build times  
B. Smaller final image size  
C. Better security through encryption  
D. Automatic versioning

---

**Q11.** Which command tags an existing image with a new name?

A. `docker image rename`  
B. `docker tag <image> <new-tag>`  
C. `docker retag`  
D. `docker image tag --new`

---

## ✅ 3. Installation and Configuration

**Q12.** Where is the Docker daemon configuration file typically located on Linux?

A. `/etc/docker/config.json`  
B. `/var/lib/docker/config.json`  
C. `/etc/docker/daemon.json`  
D. `/usr/docker/daemon.conf`

---

**Q13.** Which command sets Docker to start at boot?

A. `docker enable`  
B. `docker start`  
C. `systemctl enable docker`  
D. `docker boot-config`

---

**Q14.** What is the default logging driver for Docker?

A. `syslog`  
B. `json-file`  
C. `journald`  
D. `none`

---

**Q15.** How do you configure Docker to use a specific storage driver?

A. Set `storage-driver` in `/etc/docker/daemon.json`  
B. Use `docker config set storage-driver`  
C. Edit `/var/lib/docker/storage.conf`  
D. Pass `--storage-driver` to each `docker run` command

---

**Q16.** Which file should you edit to configure Docker daemon options persistently?

A. `~/.docker/config.json`  
B. `/etc/docker/daemon.json`  
C. `/var/lib/docker/daemon.conf`  
D. `/etc/sysconfig/docker`

---

## ✅ 4. Networking

**Q17.** Which command creates a user-defined bridge network?

A. `docker create network mynet`  
B. `docker network add mynet`  
C. `docker network create mynet`  
D. `docker net new mynet`

---

**Q18.** What is the main benefit of user-defined bridge networks over the default bridge?

A. Better CPU usage  
B. Automatic DNS resolution by container name  
C. Lower memory usage  
D. Faster startup

---

**Q19.** Which network driver is used for connecting services across multiple Docker hosts in a Swarm?

A. bridge  
B. host  
C. overlay  
D. macvlan

---

**Q20.** What does the `--publish` flag do when creating a container?

A. Makes the image available on Docker Hub  
B. Maps container ports to host ports  
C. Shares the container's network with the host  
D. Creates a new network bridge

---

**Q21.** Which command inspects the details of a Docker network?

A. `docker network show <network>`  
B. `docker network inspect <network>`  
C. `docker network details <network>`  
D. `docker inspect --network <network>`

---

**Q22.** What happens when a container is started with `--network=host`?

A. The container gets its own network namespace  
B. The container shares the host's network stack  
C. The container cannot access the network  
D. A new bridge network is created

---

## ✅ 5. Security

**Q23.** What command enables image signature verification in Docker?

A. `docker --verify-signatures`  
B. `docker trust enable`  
C. `export DOCKER_CONTENT_TRUST=1`  
D. `docker enable content-trust`

---

**Q24.** Which tool is recommended to audit Docker host security?

A. `docker secure`  
B. `docker scan`  
C. `docker-bench-security`  
D. `dockersec`  

---

**Q25.** What is the recommended way to run containers as non-root?

A. Use `--user` flag or `USER` instruction in Dockerfile  
B. Disable root in daemon.json  
C. Use `--no-root` flag  
D. Run `docker security --non-root`

---

**Q26.** Which capability should you drop to prevent a container from changing file ownership?

A. `CAP_SYS_ADMIN`  
B. `CAP_CHOWN`  
C. `CAP_NET_ADMIN`  
D. `CAP_SETUID`

---

**Q27.** Where are secrets stored in a Docker Swarm?

A. In plain text on each worker node  
B. Encrypted in the Raft log on manager nodes  
C. In `/var/lib/docker/secrets`  
D. In environment variables

---

**Q28.** What does AppArmor provide for Docker containers?

A. Network isolation  
B. Mandatory Access Control (MAC) security profiles  
C. Image encryption  
D. Volume backup

---

## ✅ 6. Storage and Volumes

**Q29.** Which command backs up a named volume using a tarball?

A. `docker volume export`  
B. `tar -czf` from a container mounting the volume  
C. `docker cp`  
D. `docker volume backup`

---

**Q30.** Which statement is true about bind mounts?

A. They are stored in Docker-managed paths.  
B. They persist beyond container deletion.  
C. They are used only in Swarm.  
D. They require a named volume.

---

**Q31.** What is the command to create a named volume?

A. `docker volume new myvolume`  
B. `docker volume create myvolume`  
C. `docker create volume myvolume`  
D. `docker volume add myvolume`

---

**Q32.** What is the default location for volumes on Linux?

A. `/var/lib/docker/volumes`  
B. `/etc/docker/volumes`  
C. `/opt/docker/volumes`  
D. `/home/docker/volumes`

---

**Q33.** Which mount type is recommended for production workloads?

A. Bind mounts  
B. tmpfs mounts  
C. Named volumes  
D. NFS mounts

---

**Q34.** How do you remove all unused volumes?

A. `docker volume rm --all`  
B. `docker volume prune`  
C. `docker volume clean`  
D. `docker system prune --volumes`

---

**Q35.** What flag mounts a volume as read-only?

A. `--volume myvolume:/data:ro`  
B. `--volume myvolume:/data --read-only`  
C. `--mount readonly,source=myvolume,target=/data`  
D. Both A and C

---

## 📖 Notes

- For answer explanations, see [`answers.md`](./answers.md).
- Randomize questions for mock exam simulations.
- Try answering from memory before checking the official docs.
