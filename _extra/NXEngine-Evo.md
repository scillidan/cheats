---
tags: game
---

## Install

### Raspberry Pi Desktop

```sh
wget https://github.com/scillidan/nxengine-evo-dist/releases/download/v2.6.5-1/NXEngine-Evo-v2.6.5-1-Linux-aarch64.AppImage
```

```sh
~/Downloads/NXEngine-Evo-v2.6.5-1-Linux-aarch64.AppImage --appimage-extract >/dev/null 2>&1
```

```sh
mkdir -p ~/.local/share/icons
cp ./usr/share/icons/hicolor/256x256/apps/org.nxengine.nxengine_evo.png ~/.local/share/icons/nxengine-evo.png
```

```sh
vim ~/.local/share/applications/nxengine-evo.desktop
```

```
[Desktop Entry]
Name=NXEngine-evo
Comment=
Exec=env LIBGL_ALWAYS_SOFTWARE=1 /home/<user>/Applications/NXEngine-Evo-v2.6.5-1-Linux-aarch64.AppImage
Icon=/home/<user>/.local/share/icons/nxengine-evo.png
Terminal=false
Type=Application
Categories=Game
StartupNotify=true
```