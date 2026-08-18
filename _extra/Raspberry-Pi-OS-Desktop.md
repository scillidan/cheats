## Firstboot

- Update Software → Skip

## Clean

```sh
sudo apt purge chromium chromium-common chromium-l10n chromium-sandbox rpi-chromium-mods
sudo apt autoremove --purge
sudo apt autoclean
```

## Install .deb

```sh
sudo apt install ./<.deb>
```

## Game

```sh
sudo apt install love
sudo apt install retroarch
```