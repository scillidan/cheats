## Disable WiFi[^1][^2]

```sh
sudo ifconfig eth0 up
sudo ifconfig wlan0 down
```

But it seems don't work.

```sh
sudo rm /etc/netplan/50-cloud-init.yaml
sudo vim /etc/netplan/00-installer-config.yaml
```

```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    eth0:
      dhcp4: true
      optional: true
  wifis:
    wlan0:
      dhcp4: true
      optional: false
      access-points:
        "<ssid>":
          password: "<password>"
          hidden: true
```

```sh
sudo chmod 600 /etc/netplan/00-installer-config.yaml
sudo netplan generate
sudo netplan --debug apply
sudo reboot
```

```sh
ip a
sudo ifconfig wlan0 down
```

## Install Nerd Font[^3]

```sh
sudo vim /etc/fonts/conf.d/50-enable-fixed.conf
```

```
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <selectfont>
    <acceptfont>
      <pattern>
        <patelt name="<font_family>"><string>fixed</string></patelt>
      </pattern>
    </acceptfont>
  </selectfont>
</fontconfig>
```

```sh
sudo dpkg-reconfigure fontconfig
```

```sh
wget https://github.com/ryanoasis/nerd-fonts/releases/download/v3.3.0/JetBrainsMono.tar.xz
tar -xJvf JetBrainsMono.tar.xz
rm README.md
rm OFL.txt
mv JetBrains** ~/.local/share/fonts
```

[^1]: [Configure a Static IP address for WIFI using Netplan in Ubuntu Server 22.04 on a HP Pavillion Desktop 510-p051a](https://stackoverflow.com/questions/77637274/configure-a-static-ip-address-for-wifi-using-netplan-in-ubuntu-server-22-04-on-a)
[^2]: [No internet connection after ubuntu server 20.04 install, ifconfig not available](https://askubuntu.com/questions/1233934/no-internet-connection-after-ubuntu-server-20-04-install-ifconfig-not-available)
[^3]: [ubuntu wiki - Fonts](https://wiki.ubuntu.com/Fonts)