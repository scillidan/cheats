## Install Pi OS on RPI-5[^1][^2]

```sh
sudo apt install rpi-imager
wget https://downloads.raspberrypi.com/raspios_lite_arm64/images/raspios_lite_arm64-2025-05-13/2025-05-13-raspios-bookworm-arm64-lite.img.xz
lsblk
sudo rpi-imager --cli --first-run-script ./firstrun.sh 2025-05-13-raspios-bookworm-arm64-lite.img.xz /dev/nvmeXnX
sudo shutdown now
```

```sh
sudo apt update
sudo apt upgrade
sudo raspi-config
```

Locallisation Options → Locale → Enter `<Space>` to select/unselect → `en_US-UTF-8 UTF-8` → OK → `en_US-UTF-8` → OK → Finish.

```sh
sudo reboot now
```
	
```sh
sudo update-locale LANGUAGE="en_US:en"
sudo update-locale LC_ALL=en_US.UTF-8
sudo reboot now
```

```sh
locale
```

## Use repository mirror

```sh
sudo cp /etc/apt/sources.list.d/debian.sources /etc/apt/sources.list.d/debian.sources.bak
sudo cp /etc/apt/sources.list.d/raspi.sources /etc/apt/sources.list.d/raspi.sources.bak
```

```sh
sudo tee /etc/apt/sources.list.d/debian.sources > /dev/null <<'EOF'
Types: deb
URIs: http://mirrors.ustc.edu.cn/debian
Suites: trixie trixie-updates
Components: main contrib non-free non-free-firmware
Signed-By: /usr/share/keyrings/debian-archive-keyring.gpg

Types: deb
URIs: http://mirrors.ustc.edu.cn/debian-security
Suites: trixie-security
Components: main contrib non-free non-free-firmware
Signed-By: /usr/share/keyrings/debian-archive-keyring.gpg
EOF
```

```sh
sudo tee /etc/apt/sources.list.d/raspi.sources > /dev/null <<'EOF'
Types: deb
URIs: http://mirrors.ustc.edu.cn/raspberrypi/debian/
Suites: trixie
Components: main
Signed-By: /usr/share/keyrings/raspberrypi-archive-keyring.pgp
EOF
```

## Install .deb

```sh
sudo dpkg -i <.deb>
```

[^1]: [Configure_OS.md](https://github.com/danielfreer/raspberrypi5-retropie-setup/blob/main/Configure_OS.md)
[^2]: [Install_RetroPie.md](https://github.com/danielfreer/raspberrypi5-retropie-setup/blob/main/Install_RetroPie.md)