---
tags: arch
---

```sh
sudo vim /etc/pacman.conf
```

```
[multilib]
Include = /etc/pacman.d/mirrorlist
```

```sh
sudo pacman -Syyu
sudo pacman -S steam
```