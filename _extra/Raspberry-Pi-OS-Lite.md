## Config

### Locale

```sh
sudo update-locale LANGUAGE="en_US:en"
sudo update-locale LC_ALL=en_US.UTF-8
sudo reboot now
```

```sh
locale
```

### Timezone

```sh
sudo timedatectl set-timezone Asia/Shanghai
```

### Keyboard

```sh
sudo raspi-config nonint do_configure_keyboard us
```

### Wi-Fi

```sh
sudo raspi-config nonint do_wifi_country CN
sudo nmcli --ask dev wifi connect '<ssid>'
```

### Enable SSH

```sh
sudo systemctl enable --now ssh
```

### Use repository mirror

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

## Update

```sh
sudo apt update
sudo apt upgrade
```