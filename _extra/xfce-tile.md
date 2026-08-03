---
tags: arch
---

```sh
sudo pacman -S python-gobject python-xlib
git clone --depth=1 https://github.com/dodophoenix/xfce-tile
cd xfce-tile
cp xfce-setup-shortcuts.sh xfce-setup-shortcuts.sh.bak
chmod +x ./xfce-setup-shortcuts.sh
# vim xfce-setup-shortcuts.sh
```

```sh
./xfce-setup-shortcuts.sh
```