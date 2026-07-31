---
tags: andriod
---

```sh
pkg update
pkg upgrade
```

About Username, see [Termux is single-user](https://wiki.termux.com/wiki/Differences_from_Linux#Termux_is_single-user).

## Via SSH

```sh
pkg install openssh
passwd
sshd
```

On PC:

```sh
ssh -p 8022 <any_username>@<your_host>
```

Then you can use your PC's keyboard and clipboard.

## [Termux-setup-storage](https://wiki.termux.com/wiki/Termux-setup-storage)

```sh
termux-setup-storage
```

## Enable Linux file system

[^1] [^2]

```sh
pkg install proot
termux-chroot
ls /usr
```

## install Opts

```sh
pkg install \
  7zip \
  atuin \
  bat \
  carapace \
  chafa \
  curl \
  eza \
  fastfetch \
  fd \
  fzf \
  gh \
  git \
  glow \
  gnupg \
  jq \
  lazygit \
  less \
  neovim \
  openssh \
  pass \
  ripgrep \
  rust \
  sdcv \
  starship \
  tmux \
  uv \
  vim \
  wget \
  yazi \
  yq \
  zoxide
```

```sh
# Cargo
cargo install --force \
  eva \
  grex \
  pipe-rename \
  thumbs
  # thes
# Pip
pip install \
  subliminal
```

## Install Nerd Font[^3]

```sh
mv <font> ~/.termux/font.ttf
termux-reload-settings
```

## Configure Keyboard[^4][^5]

```sh
cp ~/.termux/termux.properties ~/.termux/termux.properties.bak
vim ~/.termux/termux.properties
```

```
extra-keys = [[ \
  {key: TAB, popup: KEYBOARD}, \
  {key: ESC, popup: '<'}, \
  {key: CTRL, popup: '['}, \
  {key: ALT, popup: '\{'}, \
  {key: 'BACKSLASH', popup: '|'}, \
  {key: '_', popup: '='}, \
  {key: UP, popup: PGUP}, \
  {key: DOWN, popup: PGDN}, \
  {key: LEFT, popup: HOME}, \
  {key: RIGHT, popup: END} \
]]
```

## Input Method

- [copy and paste using Ctrl-C Ctrl-V or right click menu](https://github.com/termux/termux-app/issues/1891)
- [Text Input View](https://wiki.termux.com/wiki/Touch_Keyboard#Text_Input_View)

## About Desktop Environment

- [Graphical Environment](https://wiki.termux.com/wiki/Graphical_Environment)  
- [Termux Desktop](https://github.com/adi1090x/termux-desktop)  
- [termux-desktop-xfce](https://github.com/Yisus7u7/termux-desktop-xfce)

## [PRoot Distro](https://github.com/termux/proot-distro)

```sh
pkg install proot-distro
proot-distro install archlinux
proot-distro list
proot-distro login archlinux
```

## Keymap

- [Termux](https://wiki.termux.com/wiki/Touch_Keyboard)

```
termux: Paste | C-A-v
```

[^1]: [Termux is not FHS compliant](https://wiki.termux.com/wiki/Differences_from_Linux#Termux_is_not_FHS_compliant)
[^2]: [Access Termux from a file manager](https://wiki.termux.com/wiki/Internal_and_external_storage)
[^3]: [[Info] How to setup nerd font in order to work lsd properly in Termux(Android)](https://github.com/lsd-rs/lsd/issues/423)
[^4]: [Can I hide this keyboard? I have a physical one attached](https://www.reddit.com/r/termux/comments/qaenv5/can_i_hide_this_keyboard_i_have_a_physical_one/)
[^5]: [Disabling the up-arrow key rebinding?](https://github.com/atuinsh/atuin/issues/51#issuecomment-1641211422)