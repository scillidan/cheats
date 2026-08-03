## Choose a OS

- [Recalbox](https://www.recalbox.com/) used [ES-DE](https://gitlab.com/es-de/emulationstation-de) with [Modern](https://gitlab.com/es-de/themes/modern-es-de) theme
- [RetroPie](https://retropie.org.uk/) used [ES-DE](https://gitlab.com/es-de/emulationstation-de) as default frontend

## Flash OS to SD card

1. Get [SD Memory Card Formatter](https://www.sdcard.org/downloads/formatter). Use it to format SD card
2. Get [Raspberry Pi Imager](https://www.raspberrypi.com/software)
3. Raspberry Pi Imager:
	1. Raspberry Pi Device → Raspberry Pi 4
	2. 请选择需要写入的操作系统 → Emulation and game OS
	3. 储存卡 → SD card
	4. 可选配置 → 在完成后卸载磁盘 (Off)
	5. Next

## Install display patch and safe-shutdown script

1. Click `Download GPiCase2 patch` on [GPiCase2-Script](https://github.com/RetroFlag/GPiCase2-Script) to download `GPi_Case2_patch/`
2. Decompress it to `GPi_Case2_patch/`
3. Copy all files under `GPi_Case2_patch_<os>` to `<SD card>/`
4. (Windows 10) Run `Install_patch.bat`
5. Create a file `gpi.sh`
   ```sh
   wget -O - "https://raw.githubusercontent.com/RetroFlag/GPiCase2-Script/main/retropie_install_gpi2.sh" | sudo bash
   ```

## First boot

1. Insert SD card into GPi CASE 2, turn it on
2. After first boot, you can hold a button to configure keymap. You can hold any button until it is be skipped