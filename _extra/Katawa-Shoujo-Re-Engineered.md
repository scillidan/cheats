---
tags: game
---

## Install

### Raspberry Pi Desktop

```sh
wget https://github.com/fleetingheart/ksre/releases/download/v2.0.4/sh.fhs.ksre-aarch64.AppImage
```

```sh
~/Downloads/sh.fhs.ksre-aarch64.AppImage --appimage-extract >/dev/null 2>&1
```

```sh
mkdir -p ~/.local/share/icons
cp icon.svg ~/.local/share/icons/ksre.svg
```

```sh
vim ~/.local/share/applications/ksre.desktop
```

```
[Desktop Entry]
Name=Katawa Shoujo: Re-Engineered
Comment=
Exec=env LIBGL_ALWAYS_SOFTWARE=1 /home/<user>/Applications/sh.fhs.ksre-aarch64.AppImage
Icon=/home/<user>/.local/share/icons/ksre.svg
Terminal=false
Type=Application
Categories=Game
StartupNotify=true
```