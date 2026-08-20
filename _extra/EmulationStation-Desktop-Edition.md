## Install

### Raspberry Pi Desktop

Go https://es-de.org/#Download, download `Linux aarch64 AppImage`.

```sh
mkdir -p ~/Applications
cp ~/Downloads/ES-DE_aarch64.AppImage ~/Applications/ES-DE_aarch64.AppImage
chmod +x ~/Applications/ES-DE.AppImage
```

```sh
~/Downloads/ES-DE_aarch64.AppImage --appimage-extract >/dev/null 2>&1
```

```sh
mkdir -p ~/.local/share/icons
cp squashfs-root/usr/share/icons/hicolor/<icon>.svg ~/.local/share/icons/es-de.svg
```

```sh
vim ~/.local/share/applications/es-de.desktop
```

```
[Desktop Entry]
Name=ES-DE
Comment=EmulationStation Desktop Edition
Exec=env LIBGL_ALWAYS_SOFTWARE=1 /home/<user>/Applications/ES-DE_aarch64.AppImage
Icon=/home/<user>/.local/share/icons/es-de.svg
Terminal=false
Type=Application
Categories=Game;Emulator;
StartupNotify=true
```

## Add custom systems

```sh
# Linux
vim ~/.emulationstation/custom_systems/es_systems.xml
# Windows
subl ES-DE\ES-DE\custom_systems\es_systems.xml
```

```xml
<systemList>
    <system>
        <name>love</name>
        <fullname>LÖVE 2D</fullname>
        <path>%ROMPATH%/love</path>
        <extension>.love .LOVE</extension>
        <command>love "%ROM%"</command>
        <platform>love</platform>
        <theme>love</theme>
    </system>
</systemList>
```