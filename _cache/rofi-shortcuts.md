---
tags: arch
---

```sh
git clone --depth=1 https://github.com/Zeioth/rofi-shortcuts
cd rofi-shortcuts
mkdir -p ~/.config/rofi/rofi-shortcuts/
mkdir -p ~/.local/share/rofi/rofi-shortcuts/
cp ./rofi-shortcuts.conf ~/.config/rofi/rofi-shortcuts/rofi-shortcuts.conf
cp ./rofi-shortcuts.sh ~/.local/share/rofi/rofi-shortcuts/rofi-shortcuts.sh
chmod u+x ~/.local/share/rofi/rofi-shortcuts/rofi-shortcuts.sh
ln -sf ~/.local/share/rofi/rofi-shortcuts/rofi-shortcuts.sh ~/.local/bin/rofi-shortcuts
```

```sh
rofi-shortcuts
```