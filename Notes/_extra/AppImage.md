---
tags: arch
---

- Thunar → `<app>.AppImage` → Properties → Permissions → Allow this file to run as a program.
- Or `chmod +x <app>.AppImage`.

```sh
cd ~/.local/share/applications
vim <app>.desktop
```

```
[Desktop Entry]
Type=Application
Name=<The APP>
Comment=<comment>
Icon=<absolute_path_to>/icon.png
Exec=<absolute_path_to>/<app>.AppImage --appimage-portable-config
Terminal=false
Categories=<categorie_1>;<categorie_1>
Path=
StartupNotify=false
```

Launch `<app>.desktop` → Mark As Secure And Launch.

[^1]: [Registering an AppImage file as a desktop app in KDE](https://askubuntu.com/questions/902672/registering-an-appimage-file-as-a-desktop-app-in-kde)
[^2]: [How does an appimage persist settings between launches?](https://askubuntu.com/questions/1009888/how-does-an-appimage-persist-settings-between-launches)