---
description: Linux kernel driver for Xbox One and Xbox Series X|S accessories
tags: game
---

```sh
yay -S --noconfirm xone-dkms-git xone-dongle-firmware
```

Or:

```sh
git clone --depth=1 https://github.com/medusalix/xone
cd xone
sudo ./install.sh
sudo xone-get-firmware.sh
# sudo ./uninstall
```