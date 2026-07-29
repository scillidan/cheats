Install on Ubuntu 22 ARM [^1]\:

```sh
sudo apt install vsftpd
sudo vim /etc/vsftpd.conf
```

```
utf8_filesystem=YES
```

```sh
sudo systemctl enable --now vsftpd
```

[^1]: [Setting Up a Basic FTP Server on Ubuntu 22](https://reintech.io/blog/setting-up-basic-ftp-server-ubuntu-22)