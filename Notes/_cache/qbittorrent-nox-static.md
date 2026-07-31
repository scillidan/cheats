## Install on Ubuntu 22 ARM

```sh
sudo adduser qbittorrent
su qbittorrent
```

```sh
mkdir -p ~/bin && source ~/.profile
wget -qO ~/bin/qbittorrent-nox https://github.com/userdocs/qbittorrent-nox-static/releases/latest/download/aarch64-qbittorrent-nox
chmod 700 ~/bin/qbittorrent-nox
~/bin/qbittorrent-nox
```

1. The default account and password is displayed in terminal.
2. Visit `<your_host>:8080` and login.
3. qBittorrent WebUI → Settings
	- WebUI
		- Authentication → Change `Username`, `Password`.
		- (Optional) Web User Interface → Change IP address to `0.0.0.0`, change port to `8090`.
		- (Optional) Bypass authentication for clients on localhost (On).
		- (Optional) Bypass authentication for clients in whilelisted IP subnets → ...
	- Speed → Global Rate Limits → For example, you can set a lower speed here, liked `100` KiB/s upload and `10000` KiB/s download.
	- Connection → Connections Limits → Set lesser number here.
	- Advanced → Customize application instance name `Steam`.

```sh
su <sudo_user>
sudo vim /etc/systemd/system/qbittorrent.service
```

```
[Unit]
Description=qBittorrent-nox service
Documentation=man:qbittorrent-nox(1)
Wants=network-online.target
After=network-online.target nss-lookup.target

[Service]
Type=exec
User=qbittorrent
ExecStart=/home/qbittorrent/bin/qbittorrent-nox
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

```sh
sudo systemctl enable --now qbittorrent
systemctl status qbittorrent
```

## Download to mounted disk

```sh
sudo mkdir /mnt/<mount_name>/qbittorrent
sudo groupadd mountusers
sudo usermod -aG mountusers qbittorrent
## Get the uid
id -u $USER
## Get the gid
getent group mountusers
sudo cp /etc/fstab /etc/fstab.bak
sudo vim /etc/fstab
```

```sh
# Add on bottom. I used NTFS disk here.
UUID=<disk_uuid> /mnt/<mount_name> ntfs-3g default,uid=<uid>,gid=<gid>,umask=0000, 0 0
```

```sh
# sudo systemctl deamon-reload
# sudo mount -a
sudo reboot
```

qBittorrent WebUI → Settings → Downloads → Saving Management → Default Save Path → `/mnt/<mount_name>/qbittorrent`.。

## Share downloaded files via Samba

```sh
sudo vim /etc/samba/smb.conf
```

```
[qbittorrent]
comment = qbittorrent
path = /mnt/<mount_name>/share/qbittorrent
guest ok = no
read only = no
browsable = yes
writeable = yes
force user = qbittorrent
```

```sh
sudo systemctl restart smbd
```