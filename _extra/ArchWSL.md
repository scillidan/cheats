---
tags: windows
---

```sh
# scoop install archwsl
wsl --install archlinux
arch
```

```sh
passwd
echo "%wheel ALL=(ALL) ALL" > /etc/sudoers.d/wheel
useradd -m -G wheel -s /bin/bash <user>
passwd <user>
exit
```

```sh
arch config --default-user <user>
arch
```

## Optionals for WSL[^1]

### D-Bus

```sh
# sudo pacman -S dbus
sudo mkdir /run/dbus -p
sudo dbus-daemon --system
```

### systemd/systemctl

```sh
vim /etc/wsl.conf
```

```
[boot]
systemd=true
```

## Cross reference

0. [[Arch-Linux]]
1. [[WSL]]
2. [[Pacman]]
3. [[yay]]
4. [[OpenSSH]]
5. [[VNC]]

[^1]: [Known issues](https://wsldl-pg.github.io/ArchW-docs/Known-issues/)