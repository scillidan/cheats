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

```sh
sudo apt install git lsb-release
git clone --depth=1 https://github.com/RetroPie/RetroPie-Setup
cd RetroPie-Setup
chmod +x retropie_setup.sh
sudo ./retropie_setup.sh
```

1. Basic Install → Yes
2. Update → Yes

## Setup

```sh
sudo ~/RetroPie-Setup/retropie_setup.sh
# In EmulationStation, you can clink `<Start>` → RetroPie Configuration → RestroPie Setup
```

1. Configuration/tools
	- autostart → Start EmulationStation at boot → OK
	- bluetooth
		1. Pair and Connect to Bluetooth Device → `<your_controller>` → OK → DisplayYesNo
		2. (Optional) Configurate bluetooth connect mode → boot → OK
	- (Optional) wifi → Connect to WiFi network → `<your_wifi>` → Entry `<your_wifipasswd>` → Ok
	- (Optional) samba
		1. Install RetroPie Samba shares → Ok
		2. Manually edit /etc/samba/smb.conf → `workgroup = SMBGPRP`
		3. Restart Samba service
		4. Default Samba Shares and paths:
			- `roms`, `/home/user/RetroPie/roms`
			- `bios`, `/home/user/RetroPie/BIOS`
			- `configs`, `/opt/retropie/configs`
			- `splashscreens` `/home/user/RetroPie/splashscreens`
2. Perform reboot

## GPi CASE 2 setup[^5][^6]

1. Connect to a keyboard
2. `<Start>` → RetroPie (Configuration)
	- File Manager → Used `<A>` to enter, Find and run `/boot/gpi.sh`
	- WiFi → Connect to WiFi
	- (Optional) Interface Options → SSH → Yes
4. On PC, connect with:
   ```
   host `retropie` (or ip-address)
   port `22`
   username `pi`
   password `raspberry`
   ```

## Optional

### Bluetooth adapter[^3]

```sh
sudo apt install bluetooth pi-bluetooth bluez
sudo vim /boot/firmware/config.txt
```

```
# Add on bottom
[all]
dtoverlay=disable-bt
```

```sh
sudo reboot
```

### Enable Xbox controller adapter[^4]

```sh
git clone --depth=1 https://github.com/medusalix/xow
cd xow
make BUILD=RELEASE
sudo make install
sudo apt install cabextract
chmod +x ./firmware.sh
sudo ./firmware.sh
sudo systemctl enable --now xow
sudo systemctl status xow
# sudo systemctl stop xow
# sudo systemctl disable xow
# sudo make uninstall
```

### Enable Pegasus Frontend[^7]

1. RetroPie (Configuration) → RetroPie Setup → Configuration/tools
	1. Manage packages → Manage experimental packages → `pegasus-fe` → Install from pre-compiled binary
	2. autostart → Manally edit /opt/retropie/configs/all/autostart.sh → `pegasus-fe`
2. Reboot

### Emulator Löve (Experimental)[^8][^9]

1. RetroPie (Configuration) → RetroPie Setup → Manage packages → Manage optional packages → `love-0.10.2` or `love`
2. Add `<game>.love` `<path_to>/roms/love/`

## Usage

1. Configure keymap: `<Start>` → Main Menu → Configure Input → Hold a key on controller to set
2. Refresh roms: `<Start>` → Main Menu → Quit → Restart EmulationStation → Game listing will be refreshing

[^1]: [Configure_OS.md](https://github.com/danielfreer/raspberrypi5-retropie-setup/blob/main/Configure_OS.md)
[^2]: [Install_RetroPie.md](https://github.com/danielfreer/raspberrypi5-retropie-setup/blob/main/Install_RetroPie.md)
[^3]: [Bluetooth on the Raspberry](https://pimylifeup.com/raspberry-pi-bluetooth/)
[^4]: [xow](https://github.com/medusalix/xow)
[^5]: [Retro Gaming With RetroPie, GPi CASE 2, and a Raspberry Pi](https://navendu.me/posts/retropie-gpi-case-2-setup/)
[^6]: [RetroPie - SSH](https://retropie.org.uk/docs/SSH/)
[^7]: [Pegasus Docs - Platform Notes: Raspberry](https://pegasus-frontend.org/docs/user-guide/platform-raspberry/#retropie)
[^8]: [RetroPie Docs - Love](https://retropie.org.uk/docs/Love/)
[^9]: [PyGame LÖVE (love2d) in RecalBox](https://forum.recalbox.com/topic/19222/pygame-l%C3%B6ve-love2d-in-recalbox)