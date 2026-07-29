## Install on Arch[^1]

```sh
sudo pacman -S fcitx5-im fcitx5-gtk fcitx5-qt fcitx5-rime
```

```sh
vim ~/.xprofile
```

```
export GTK_IM_MODULE="fcitx"
export QT_IM_MODULE="fcitx"
export XMODIFIERS="@im=fcitx"
export INPUT_METHOD="fcitx"
export XIM="fcitx"
export XIM_PROGRAM="fcitx"
export SDL_IM_MODULE="fcitx"
export GLFW_IM_MODULE="ibus"
```

Then reboot.

- Xfce → Setttings → Fcitx 5 Configuration
	- Input Method → Available Input Method → Select `Rime` → Move to left.
	- Global Options → Trigger Input Method → `Shift` → Apply.