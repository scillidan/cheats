---
tags: arch
---

```sh
sudo pacman -S bluez bluez-utils blueman
sudo systemctl enable --now bluetooth
```

## usage

```sh
# rfkill list
# sudo rfkill unblock bluetooth
# sudo hciconfig hci0 up
# hciconfig
bluetoothctl
```

```sh
# bluetoothctl
scan on
pair XX:XX:XX:XX:XX:XX
connect XX:XX:XX:XX:XX:XX
trust XX:XX:XX:XX:XX:XX
```

[^1]: [Bluetooth headset connection occasionally fails: br-connection-page-timeout](https://www.reddit.com/r/archlinux/comments/qnffce/bluetooth_headset_connection_occasionally_fails/)
[^2]: [How to Set up Bluetooth in Arch Linux](https://www.jeremymorgan.com/tutorials/linux/how-to-bluetooth-arch-linux/)