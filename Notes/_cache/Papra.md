---
description: The minimalistic document archiving platform
tags: docker
---

```sh
# https://docs.papra.app/self-hosting/using-docker-compose
mkdir papra
cd papra
vim docker-compose.yml
```

```yaml
services:
  papra:
    container_name: papra
    image: ghcr.io/papra-hq/papra:latest
    restart: unless-stopped
    ports:
      - "1221:1221"
    volumes:
      - /mnt/<mount_disk>/share/papra/app-data:/app/app-data
    user: "${UID}:${GID}"
```