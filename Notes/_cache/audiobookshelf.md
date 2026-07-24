---
description: Self-hosted audiobook and podcast server
tags: docker
---

```sh
# https://www.audiobookshelf.org/docs/#docker-compose-install
mkdir audiobookshelf
cd audiobookshelf
vim docker-compose.yml
# Copy from https://github.com/advplyr/audiobookshelf/blob/master/docker-compose.yml
```

```yaml
volumes:
  # Add media dirs on mount disk
  - /mnt/<mount_name>/audiobookshelf:/audiobooks
  - /mnt/<mount_name>/podcast:/podcasts
```

```sh
sudo docker compose up -d
```