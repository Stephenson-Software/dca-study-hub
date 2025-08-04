# 🧪 Docker CLI Command Reference

This file lists frequently used Docker commands organized by category. Use this as a quick lookup during study sessions and hands-on practice.

---

## 🐳 Container Lifecycle

```bash
docker run -d --name mycontainer nginx        # Run a container in detached mode
docker ps                                      # List running containers
docker ps -a                                   # List all containers (including exited)
docker stop mycontainer                        # Stop a running container
docker start mycontainer                       # Start a stopped container
docker restart mycontainer                     # Restart a container
docker rm mycontainer                          # Remove a container
docker logs mycontainer                        # View container logs
docker exec -it mycontainer bash               # Enter a running container
docker attach mycontainer                      # Attach to container STDOUT
```

---

## 📦 Image Management

```bash
docker build -t myimage .                      # Build image from Dockerfile
docker images                                  # List local images
docker tag myimage myrepo/myimage:1.0          # Tag an image
docker push myrepo/myimage:1.0                 # Push image to registry
docker pull nginx                              # Pull image from registry
docker rmi myimage                             # Remove an image
docker image history myimage                   # Show image layer history
docker image inspect myimage                   # Detailed metadata
```

---

## 📁 Volumes & Data

```bash
docker volume create myvolume                  # Create named volume
docker volume ls                               # List volumes
docker volume inspect myvolume                 # Inspect volume details
docker volume rm myvolume                      # Remove volume
docker run -v myvolume:/data nginx             # Mount named volume
docker run -v $(pwd):/app myimage              # Bind mount current dir
```

---

## 🌐 Networking

```bash
docker network create mynet                    # Create user-defined bridge network
docker network ls                              # List networks
docker network inspect mynet                   # Inspect a network
docker run --network mynet nginx               # Run container on custom network
docker run -p 8080:80 nginx                    # Publish container port
```

---

## 🐝 Swarm Mode

```bash
docker swarm init                              # Initialize Swarm cluster
docker node ls                                 # List Swarm nodes
docker service create --name web nginx         # Create a service
docker service ls                              # List services
docker service ps web                          # Tasks of a service
docker service update --image nginx:1.25 web   # Update a service
docker service scale web=3                     # Scale service
docker service rm web                          # Remove service
```

---

## 🛠 Docker Compose

```bash
docker compose up -d                           # Start all services
docker compose down                            # Stop and remove services
docker compose logs -f                         # View logs
docker compose ps                              # List running containers
```

> Ensure Docker Compose V2 is installed (`docker compose`, not `docker-compose`)

---

## 🔐 Security

```bash
docker scan myimage                            # Scan image for vulnerabilities
docker run --cap-drop=ALL nginx                # Drop all capabilities
export DOCKER_CONTENT_TRUST=1                  # Enable content trust
```

---

## 🧹 Cleanup & System

```bash
docker system df                               # Show disk usage
docker system prune                            # Remove unused data
docker image prune                             # Remove dangling images
docker volume prune                            # Remove unused volumes
docker container prune                         # Remove stopped containers
```

---

## 🧠 Tips

- Use `--help` after any command for options: `docker run --help`
- Use `docker context` to switch between remote/local environments
- Pipe commands with `jq` for filtered output:  
  `docker inspect nginx | jq '.[0].Config.Env'`

---

## 📖 References

- [Docker CLI Reference](https://docs.docker.com/engine/reference/commandline/docker/)
- [Docker Cheat Sheet (PDF)](https://dockerlabs.collabnix.com/docker/cheatsheet/)
