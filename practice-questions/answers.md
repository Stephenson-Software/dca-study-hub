# ✅ Multiple Choice Practice – Answer Key & Explanations

This document provides answers and explanations for the practice questions in [`multiple-choice.md`](./multiple-choice.md).

---

## 1. Orchestration

**Q1.** ✅ C – `docker swarm init`  
> Initializes a new Swarm cluster on the current node.

**Q2.** ✅ D – `docker stack deploy -c <file> <name>`  
> Used to deploy multi-service applications to a Swarm using a Compose file.

---

## 2. Image Creation, Management, and Registry

**Q3.** ✅ C – `.dockerignore`  
> Prevents unnecessary files from being included in the image build context.

**Q4.** ✅ A – `RUN`  
> Combining shell commands in a single `RUN` instruction helps reduce image layers and size.

---

## 3. Installation and Configuration

**Q5.** ✅ C – `/etc/docker/daemon.json`  
> This is the standard config file for persistent daemon settings on Linux.

**Q6.** ✅ C – `systemctl enable docker`  
> Ensures the Docker service starts automatically at system boot (on systemd-based Linux).

---

## 4. Networking

**Q7.** ✅ C – `docker network create mynet`  
> This command creates a user-defined bridge network.

**Q8.** ✅ B – Automatic DNS resolution by container name  
> User-defined bridge networks enable built-in container name resolution (default bridge does not).

---

## 5. Security

**Q9.** ✅ C – `export DOCKER_CONTENT_TRUST=1`  
> This environment variable enables content trust for signed image verification.

**Q10.** ✅ C – `docker-bench-security`  
> A community-maintained script that audits Docker host configurations against best practices.

---

## 6. Storage and Volumes

**Q11.** ✅ B – `tar -czf` from a container mounting the volume  
> The common pattern is to mount the volume and run `tar` inside the container to back up data.

**Q12.** ✅ B – They persist beyond container deletion  
> Bind mounts point to specific host paths and are not managed or deleted by Docker.

---

## 📌 Summary

- 12 questions across all 6 domains  
- Match your answers before exam day to test retention  
- Revisit notes or docs for any incorrect answers
