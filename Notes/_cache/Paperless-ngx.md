```sh
mkdir -v ~/paperless-ngx
wget https://raw.githubusercontent.com/paperless-ngx/paperless-ngx/refs/heads/main/docker/compose/docker-compose.postgres.yml -O docker-compose.yml
```

Add volumes as additional storage liked:

```sh
vim docker-compose.yml
```

```yaml
    volumes:
      - /mnt/nvme/paper:/usr/src/paperless/consume
```

```sh
wget https://raw.githubusercontent.com/paperless-ngx/paperless-ngx/refs/heads/main/docker/compose/docker-compose.env
vim docker-compose.env
```

```
PAPERLESS_OCR_LANGUAGES=chi-sim chi-sim-vert chi-tra chi-tra-vert
PAPERLESS_SECRET_KEY=<secret_key>
```

```sh
docker compose pull
sudo docker compose run --rm webserver createsuperuser
sudo docker compose up -d
```

[^1]: [Docker using the Installation Script](https://docs.paperless-ngx.com/setup/#docker_script)
[^2]: [Paperless-ngx - Bare Metal Route](https://docs.paperless-ngx.com/setup/#bare_metal)