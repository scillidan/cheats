---
tags: arch
---

## (Un)mount in Thunar

```sh
# sudo pacman -S gvfs-smb
logout
# Re-login
```

## Mount NTFS disk

```sh
sudo pacman -S ntfs-3g
sudo mkdir /mnt/<mount_name>
# Be careful not to format the other drive.
lsblk
sudo mount -t ntfs-3g /dev/<disk_partition> /mnt/<mount_name>
sudo blkid
sudo mount -t ntfs-3g UUID=<disk_partition_uuid> /mnt/<mount_name>
```

## Mount NTFS disk on boot

```sh
# Get the uid
id -u $USER
sudo cp /etc/fstab /etc/fstab.bak
sudo vim /etc/fstab
```

```sh
UUID=<disk_uuid> /mnt/<mount_name> ntfs-3g default,uid=<uid> 0 0
```

## Mount Samba Share

```sh
sudo pacman -S cifs-utils
sudo mkdir /mnt/<mount_name>
sudo mount -t cifs //<your_host>/<share_name> /mnt/<mount_name> -o username=<smb_user>,password=<smb_passwd>
```

## Mount Samba Share after boot

```sh
vim <path_to>/smb_credentials
```

```
username=<smbuser>
password=<smbuser_passwd>
```

```sh
chmod 600 <path_to>/smb_credentials
```

```sh
vim ~/mount.sh
```

```bash
#!/bin/bash
bin/mount -t cifs //<your_host>/<share_name> /mnt/<mount_name> -o uid=1000,gid=1000,credentials=<path_to>/smb_credentials,file_mode=0664,dir_mode=0775
```

```sh
chmod +x ~/mount.sh
sudo vim ~/.config/systemd/system/mount.service
```

```
[Unit]
Description=Mount
After=network.target

[Service]
Type=oneshot
ExecStart=/home/<user>/mount.sh
ExecStop=/bin/umount /mnt/<mount_name>
RemainAfterExit=yes

[Install]
WantedBy=default.target
```

```sh
# sudo systemctl enable --now mount-smb.service
sudo systemctl daemon-reload
sudo mount -a
sudo systemctl enable mount.service
```