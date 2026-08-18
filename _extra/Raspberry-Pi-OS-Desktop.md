## Firstboot

- Update Software → Skip

## Clean

```sh
sudo apt purge chromium chromium-common chromium-l10n chromium-sandbox rpi-chromium-mods vlc
sudo apt autoremove --purge -y
sudo apt autoclean
```

## Install .deb

```sh
sudo apt install ./<.deb>
```

## Install

```sh
sudo apt install qutebrowser mpv
sudo apt install love
sudo apt install retroarch
```