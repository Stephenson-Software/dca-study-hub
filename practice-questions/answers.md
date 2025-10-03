# ✅ Multiple Choice Practice – Answer Key & Explanations

This document provides answers and explanations for the practice questions in [`multiple-choice.md`](./multiple-choice.md).

---

## 1. Orchestration

**Q1.** ✅ C – `docker swarm init`  
> Initializes a new Swarm cluster on the current node.

**Q2.** ✅ D – `docker stack deploy -c <file> <name>`  
> Used to deploy multi-service applications to a Swarm using a Compose file.

**Q3.** ✅ D – Both A and C  
> Both `docker service scale web=5` and `docker service update --replicas 5 web` are valid commands to scale a service. The `scale` command is a shortcut for the `update --replicas` approach.

**Q4.** ✅ A – `docker node promote <node-id>`  
> This command promotes a worker node to a manager role in the Swarm cluster. The inverse command is `docker node demote`.

**Q5.** ✅ B – Services automatically restart failed tasks  
> Docker Swarm services have built-in restart policies and will automatically restart failed tasks to maintain the desired replica count. Services can run on both manager and worker nodes.

---

## 2. Image Creation, Management, and Registry

**Q6.** ✅ C – `.dockerignore`  
> Prevents unnecessary files from being included in the image build context.

**Q7.** ✅ A – `RUN`  
> Combining shell commands in a single `RUN` instruction helps reduce image layers and size.

**Q8.** ✅ B – COPY dependencies file, RUN install dependencies, COPY code  
> This order optimizes Docker's layer caching. Dependencies change less frequently than application code, so installing dependencies first allows subsequent builds to use cached layers when only code changes.

**Q9.** ✅ A – `docker image prune`  
> This command removes dangling images (untagged images that are not referenced by any container). Use `-a` flag to remove all unused images, not just dangling ones.

**Q10.** ✅ B – Smaller final image size  
> Multi-stage builds allow you to use build tools and dependencies in early stages and copy only the final artifacts to the runtime image, significantly reducing the final image size.

**Q11.** ✅ B – `docker tag <image> <new-tag>`  
> This command creates a new tag for an existing image. The format is `docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]`.

---

## 3. Installation and Configuration

**Q12.** ✅ C – `/etc/docker/daemon.json`  
> This is the standard config file for persistent daemon settings on Linux.

**Q13.** ✅ C – `systemctl enable docker`  
> Ensures the Docker service starts automatically at system boot (on systemd-based Linux).

**Q14.** ✅ B – `json-file`  
> The `json-file` logging driver is Docker's default. It stores logs in JSON format on the host filesystem. Other drivers include `syslog`, `journald`, `gelf`, and `fluentd`.

**Q15.** ✅ A – Set `storage-driver` in `/etc/docker/daemon.json`  
> The storage driver should be configured in the daemon configuration file. Example: `{"storage-driver": "overlay2"}`. Common drivers include `overlay2`, `aufs`, `devicemapper`, and `btrfs`.

**Q16.** ✅ B – `/etc/docker/daemon.json`  
> This is the standard location for persistent Docker daemon configuration on Linux. Changes require restarting the Docker daemon to take effect.

---

## 4. Networking

**Q17.** ✅ C – `docker network create mynet`  
> This command creates a user-defined bridge network.

**Q18.** ✅ B – Automatic DNS resolution by container name  
> User-defined bridge networks enable built-in container name resolution (default bridge does not).

**Q19.** ✅ C – overlay  
> Overlay networks enable communication between services across multiple Docker hosts in a Swarm cluster. They use VXLAN to encapsulate traffic.

**Q20.** ✅ B – Maps container ports to host ports  
> The `--publish` or `-p` flag maps a container port to a host port, making the service accessible from outside the container. Format: `-p host_port:container_port`.

**Q21.** ✅ B – `docker network inspect <network>`  
> This command displays detailed information about a network, including connected containers, network configuration, and driver settings.

**Q22.** ✅ B – The container shares the host's network stack  
> With `--network=host`, the container doesn't get its own IP address and uses the host's network directly. This provides better performance but less isolation.

---

## 5. Security

**Q23.** ✅ C – `export DOCKER_CONTENT_TRUST=1`  
> This environment variable enables content trust for signed image verification.

**Q24.** ✅ C – `docker-bench-security`  
> A community-maintained script that audits Docker host configurations against best practices.

**Q25.** ✅ A – Use `--user` flag or `USER` instruction in Dockerfile  
> Running containers as non-root is a security best practice. You can specify a user with `docker run --user 1000` or add `USER nonroot` in your Dockerfile.

**Q26.** ✅ B – `CAP_CHOWN`  
> The `CAP_CHOWN` capability allows changing file ownership. Dropping it with `--cap-drop=CHOWN` prevents containers from using the `chown` command.

**Q27.** ✅ B – Encrypted in the Raft log on manager nodes  
> Secrets in Swarm are encrypted at rest in the Raft log on manager nodes and encrypted in transit. They are only decrypted and mounted in-memory on containers that need them.

**Q28.** ✅ B – Mandatory Access Control (MAC) security profiles  
> AppArmor is a Linux kernel security module that provides MAC. Docker can load AppArmor profiles to restrict container capabilities and access to system resources.

---

## 6. Storage and Volumes

**Q29.** ✅ B – `tar -czf` from a container mounting the volume  
> The common pattern is to mount the volume and run `tar` inside the container to back up data.

**Q30.** ✅ B – They persist beyond container deletion  
> Bind mounts point to specific host paths and are not managed or deleted by Docker.

**Q31.** ✅ B – `docker volume create myvolume`  
> This command creates a new named volume that can be mounted to containers. Volumes are managed by Docker and stored in `/var/lib/docker/volumes` on Linux.

**Q32.** ✅ A – `/var/lib/docker/volumes`  
> This is the default location where Docker stores volume data on Linux systems. Each volume gets its own subdirectory within this path.

**Q33.** ✅ C – Named volumes  
> Named volumes are recommended for production because they are managed by Docker, provide better performance than bind mounts, work across different host operating systems, and can be backed up or migrated easily.

**Q34.** ✅ B – `docker volume prune`  
> This command removes all unused volumes (volumes not attached to any containers). To remove all volumes including unused ones as part of system cleanup, use `docker system prune --volumes`.

**Q35.** ✅ D – Both A and C  
> Both syntaxes work for read-only mounts. The `-v` or `--volume` flag uses `:ro` suffix, while the `--mount` flag uses the `readonly` option. The `--mount` syntax is more explicit and recommended.

---

## 📌 Summary

- 35 questions across all 6 domains  
- Match your answers before exam day to test retention  
- Revisit notes or docs for any incorrect answers
