---
tags: arch
---

```sh
sudo pacman -S flatpak
sudo reboot
```

```sh
flatpak remote-add --if-not-exists --user flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```

```sh
flatpak install flathub <application_id>
flatpak uninstall <application_id>
flatpak list --app
```