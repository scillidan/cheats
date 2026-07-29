---
tags: arch
---

```sh
sudo pacman -S firewalld
```

```sh
sudo systemctl enable --now firewalld
```

```sh
# Optional
sudo firewall-cmd --get-default-zone
sudo firewall-cmd --list-all-zones
sudo firewall-cmd --zone=home --list-all
```

```sh
ip a
sudo firewall-cmd --zone=home --change-interface={<wired_interface>,<wireless_interface>}
sudo firewall-cmd --get-services
sudo firewall-cmd --permanent --zone=home --add-service={ftp,samba,samba-dc,vnc-server}
# docker ps
# sudo firewall-cmd --zone=home --add-port=<docker_port>/tcp --permanent
sudo firewall-cmd --set-default-zone=home
sudo firewall-cmd --reload
sudo firewall-cmd --zone=home --list-all
```

```sh
sudo firewall-cmd --zone=work --list-all
sudo firewall-cmd --zone=work --change-interface=<wired_interface>
sudo firewall-cmd --permanent --zone=work --add-service=vnc-server
sudo firewall-cmd --reload
sudo firewall-cmd --set-default-zone=work
sudo firewall-cmd --zone=work --list-all
```