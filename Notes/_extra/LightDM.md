---
tags: arch
---

```sh
# Intel + NVIDIA
sudo pacman -S lightdm lightdm-gtk-greeter
```

```sh
# AMD
sudo pacman -S lightdm lightdm-webkit2-greeter
```

```sh
git clone --depth=1 https://github.com/TheTerrior/lightdm-minimal
cd lightdm-minimal
chmod +x ./risky_installer.sh
sudo ./risky_installer.sh
sudo vim /etc/lightdm/lightdm.conf
```

```
# Add this under [Seat:*]
greeter-session=lightdm-webkit2-greeter
```

```sh
sudo vim /etc/lightdm/lightdm-webkit2-greeter.conf
```

```
webkit_theme = minimal
```

```sh
sudo systemctl enable --now lightdm
```

[^1]: [Arch linux install lightdm (Light Display Manager)](https://gist.github.com/miguelmota/5087fb8d92599efc4748c134846c8daf)
[^2]: [A minimal LightDM WebKit2 theme](https://github.com/TheTerrior/lightdm-minimal)