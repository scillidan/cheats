## From source

```sh
git clone --depth=1 https://github.com/LibreTranslate/LibreTranslate
cd LibreTranslate
uv venv .venv --python 3.10
source .venv/bin/activate
uv pip install -e .
# libretranslate --load-only en,zh
libretranslate
# Exit
sudo cp -r ~/.local/share/argos-translate/packages /root/.local/share/argos-translate/
```

```sh
sudo vim /etc/systemd/system/libretranslate.service
```

```
[Unit]
Description=libretranslate
After=syslog.target network.target

[Service]
WorkingDirectory=/home/<user>/<path_to>/libretranslate
ExecStart=/home/<user>/<path_to>/libretranslate/.venv/bin/python main.py --host 0.0.0.0
Restart=always
RestartSec=120

[Install]
WantedBy=multi-user.target
```

```sh
sudo systemctl enable --now libretranslate
# You may have to wait a few minutes until you can visit in browser.
```

## With Docker[^1]

```sh
git clone --depth=1 https://github.com/LibreTranslate/LibreTranslate
cd LibreTranslate
mv docker-compose.yml docker-compose.yml.bak
vim docker-compose.yml
```

```yaml
services:
  libretranslate:
    container_name: libretranslate
    build:
      context: .
      dockerfile: ./docker/Dockerfile
    restart: unless-stopped
    ports:
      - "5000:5000"
    healthcheck:
      test: ['CMD-SHELL', './venv/bin/python scripts/healthcheck.py']
    environment:
      LT_HOST: 0.0.0.0
      LT_UPDATE_MODELS: 'true'
      LT_LOAD_ONLY: en,zh
    volumes:
      - libretranslate_api_keys:/app/db
      # Keep the models in a docker volume, to avoid re-downloading on startup
      - /mnt/<mount_name>/share/libretranslate_models:/home/libretranslate/.local:rw

volumes:
  libretranslate_api_keys:
  libretranslate_models:
```

```sh
sudo docker compose up -d
```

[^1]: [Where are the language models saved?](https://github.com/LibreTranslate/LibreTranslate?tab=readme-ov-file#where-are-the-language-models-saved)