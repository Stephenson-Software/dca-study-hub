# ✅ Exam Objective 6: Storage and Volumes (10%)

This section focuses on how Docker handles data persistence using volumes and bind mounts, their lifecycle, and data backup/restore strategies.

---

## 📦 Volume Types

| Type         | Description |
|--------------|-------------|
| **Named Volume** | Managed by Docker, stored in `/var/lib/docker/volumes` |
| **Bind Mount**    | Maps a specific host path to the container |
| **tmpfs**         | In-memory filesystem, removed after container stops |

---

## 🔧 Create and Use Volumes

### Create a Named Volume

```bash
docker volume create myvolume
```

### Use Volume in a Container

```bash
docker run -v myvolume:/app/data nginx
```

### Anonymous Volume

```bash
docker run -v /data nginx
```

---

## 📂 Bind Mounts

Mount a host directory into a container:

```bash
docker run -v /host/path:/container/path nginx
```

Useful for development or when you need access to specific files on the host.

---

## 🔍 Inspect and Manage Volumes

### List Volumes

```bash
docker volume ls
```

### Inspect a Volume

```bash
docker volume inspect myvolume
```

### Remove a Volume

```bash
docker volume rm myvolume
```

> ⚠️ You cannot remove volumes that are in use.

---

## 🧬 Volume Lifecycle

- Named volumes are **not deleted** when the container is removed (unless `--volumes` is used).
- Bind mounts are managed by the **host OS**, not Docker.
- Anonymous volumes are created automatically and may be harder to manage.

---

## 💾 Backup and Restore Volume Data

### Backup a Volume

```bash
docker run --rm \
  -v myvolume:/volume \
  -v $(pwd):/backup \
  alpine \
  tar czf /backup/backup.tar.gz -C /volume .
```

### Restore a Volume

```bash
docker run --rm \
  -v myvolume:/volume \
  -v $(pwd):/backup \
  alpine \
  tar xzf /backup/backup.tar.gz -C /volume
```

---

## 🧰 Volume Drivers

Third-party volume drivers can be used (e.g., NFS, cloud storage):

```bash
docker volume create \
  --driver vieux/sshfs \
  -o sshcmd=user@host:/path \
  sshvolume
```

Use when persisting data across nodes or integrating with remote storage.

---

## 🧪 Practice Prompts

- Create a volume and verify it's mounted to a container
- Use a bind mount to edit files in real time on the host
- Backup volume contents and restore them to a new volume
- List and inspect existing volumes
- Remove unused/unnamed volumes with `docker volume prune`

---

## 📌 Summary

| Task                     | Command |
|--------------------------|---------|
| Create volume            | `docker volume create` |
| Use volume               | `-v volume:/path` |
| Use bind mount           | `-v /host/path:/container/path` |
| Inspect volume           | `docker volume inspect` |
| Backup/restore           | `tar` inside container |
| Clean up volumes         | `docker volume prune` |

---

## 📖 References

- [Volumes Overview](https://docs.docker.com/storage/volumes/)
- [Bind Mounts](https://docs.docker.com/storage/bind-mounts/)
- [Backup and Restore Volumes](https://docs.docker.com/storage/volumes/#backup-restore-or-migrate-data-volumes)
- [Volume Drivers](https://docs.docker.com/storage/volumes/#use-a-volume-driver)
