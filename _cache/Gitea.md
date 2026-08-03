Get `gitea-*-linux-arm64` from [dl.gitea.com](https://dl.gitea.com/gitea).

```sh
# Ubuntu 24 ARM
gpg --keyserver keys.openpgp.org --recv 7C9E68152594688862D62AF62D9AE806EC1592E2
gpg --verify gitea-*-linux-amd64.asc gitea-*-linux-amd64
mv gitea-*-linux-arm64 gitea
sudo chmod +x gitea
sudo adduser --system --shell /bin/bash --gecos 'Git Version Control' --group --disabled-password --home /home/git git
sudo mkdir -p /var/lib/gitea/{custom,data,log}
sudo chown -R git:git /var/lib/gitea/
sudo chmod -R 750 /var/lib/gitea/
sudo mkdir /etc/gitea
sudo chown root:git /etc/gitea
sudo chmod 770 /etc/gitea
sudo cp gitea /usr/local/bin/gitea
sudo vim /etc/systemd/system/gitea.service
```

```
[Unit]
Description=Gitea
After=network.target

[Service]
User=git
Group=git
WorkingDirectory=/var/lib/gitea/
Environment=GITEA_WORK_DIR=/var/lib/gitea/
ExecStart=/usr/local/bin/gitea web -c /etc/gitea/app.ini
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
```

```sh
sudo systemctl start --now gitea.service
sudo chmod 750 /etc/gitea
sudo chmod 640 /etc/gitea/app.ini
```

[^1]: [Installation from binary](https://docs.gitea.com/installation/install-from-binary)