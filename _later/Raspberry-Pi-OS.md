---
description: 
tags: os
---

## Install[^1]

```sh
sudo apt update
sudo apt full-upgrade
sudo reboot
```

```sh
sudo rpi-update
sudo reboot
```

```sh
sudo rpi-eeprom-update
```

```sh
sudo apt install vim
sudo vim /boot/firmware/config.txt
```

```
# Add on bottom
[all]
# dtoverlay=disable-wifi
# dtoverlay=disable-bt
# dtparam=pciex1_gen=3
dtparam=cooling_fan=on
```

## Use repository mirror (Optional)[^2]

```sh
sudo cp /etc/apt/sources.list.d/raspi.list /etc/apt/sources.list.d/raspi.list.bak
sudo nano /etc/apt/sources.list.d/raspi.list
```

```
deb https://mirrors.ustc.edu.cn/debian bullseye main contrib non-free
# deb-src https://mirrors.ustc.edu.cn/debian bullseye main contrib non-free
deb https://mirrors.ustc.edu.cn/debian bullseye-updates main contrib non-free
# deb-src https://mirrors.ustc.edu.cn/debian bullseye-updates main contrib non-free
# deb https://mirrors.ustc.edu.cn/debian bullseye-backports main contrib non-free
# deb-src https://mirrors.ustc.edu.cn/debian bullseye-backports main contrib non-free
```

[^1]: [Installing Raspberry Pi OS on an NVMe SSD (Command-Line Style)](https://wolfpaulus.com/rp5-cli/)
[^2]: [USTC Mirror Help - Raspbian](https://mirrors.ustc.edu.cn/help/raspbian.html)