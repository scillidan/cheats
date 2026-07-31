---
tags: arch
---

## Install[^1]

```sh
sudo pacman -S xfce4 xfce4-goodies
# flatpak install flathub io.github.fabrialberio.pinapp
```

## Config

### Configure theme ([Materia](https://github.com/nana-4/materia-theme)) { #configure-theme }

```sh
sudo pacman -S materia-gtk-theme
```

Settings → Appearance → Style → Materia-dark-compact.

### Configure icon ([Papirus](https://github.com/PapirusDevelopmentTeam/papirus-icon-theme)) { #configure-icon }

```sh
sudo pacman -S papirus-icon-theme
```

Settings → Appearance → Icons → Papirus-Dark.

## Configure font

```sh
sudo pacman -S \
	noto-fonts-cjk \
 	noto-fonts-emoji \
 	noto-fonts-extra
```

[^2]

```sh
mkdir -p ~/.local/share/fonts/ttf
mv *.ttf ~/.local/share/fonts/ttf/<dir>/
fc-cache
```

Settings → Appearance → Style → Fonts.

## Configure cursor

```sh
mkdir ~/.icons
cd ~/.icons
```

```sh
wget https://github.com/ful1e5/Bibata_Cursor_Rainbow/releases/download/v1.1.2/Bibata-Rainbow-Modern.tar.gz
wget https://github.com/ful1e5/Bibata_Cursor_Rainbow/releases/download/v1.1.2/Bibata-Rainbow-Original.tar.gz
tar -xvf Bibata-Rainbow-Modern.tar.gz
tar -xvf Bibata-Rainbow-Original.tar.gz
```

Get `Chroma-*.tar.xz` from [Chroma Cursors for Linux](https://www.gnome-look.org/p/2045954).

```sh
tar -xvf Chroma-Black-M.tar.xz
tar -xvf Chroma-Black-S.tar.xz
tar -xvf Chroma-White-M.tar.xz
tar -xvf Chroma-White-S.tar.xz
```

Settings → Mouse and Touchpad → Theme → `<theme>`.

### Configure desktop

Settings → Desktop → Desktop Icons → Icon type → None.

### Configure thunar

- Thunar → View
	- Show Hidden Files (On)
	- Configure Toolbar
		- New Tab (On)
		- Split View (On)
		- View Switcher (On)

### Configure screensaver

- Settings → Xfce Screensaver
	- Lock Screen → Enable Lock Screen (Off)
	- Screensaver → Enable Screensaver (On/Off)

### Configure applications menu

- Settings → Panel
	- Panel 2 → Remove
	- Panel 1
	- Appearance
		- Background → Style → Solid color
		- Color → Black
	- Items
		- Separator → Expand (Off)
		- Applications Menu
			- Show button title (Off)
			- Icon → Select icon from → Image Files → `100x100.png`
		- Separator → Expand (Off)
		- Workspace Switcher
			- Appearance → Buttons
			- Workspace Settings → General → Names
				```
				# Workspace Name
				1 1
				2 2
				3 3
				4 4
				```
		- Windows Buttons
			- Show button labels (Off)
			- Show handle (Off)
		- Separator → Expand (On)
		- PulseAudio Plugin
		- Separator → Expand (On)
		- Notification Plugin
			- Hide panel button when no unread notifications
		- Status Tray Plugin
			- Adjust size automatically (On)
			- Arrange items in a single row (On)
		- Clock
			- Timezone → Asia/Shanghai
			- Layout → Time Only
		- Weather Update
			- Location name → Location name → `<your_country_or_region>`
				- Appearance → Icon theme → Liquid Dark
		- Separator → Expand (Off)
		- (Optional) Verve Command Line
		- (Optional) Clipman
		- (Optional) Directory Menu
		- (Optional) Mail Watcher
		- (Optional) Mount devices
		- (Optional) Power Mananger Plugin
		- (Optional) SmartBookmark
		- (Optional) Time Out
			- Display icon (Off)

## Default applications

Settings → Settings Manager → Default Applications.

## Window Manager

- Settings
	- Windows Manager
		- Style → Materia-dark-compact
		- Keyboard[^2]
	- Windows Manager Tweaks
		- Accessibility
			- Key used to grab and move windows → `Super`

## Others

- Storage → Removable Storage
  - Mount removable drives when hot-plugged (On)
  - Mount removable media when inserted (On)

## Backup xfce configure

```sh
git add ~/.config/xfce4
```

Or:

```sh
git add \
	~/.config/xfce4/xfconf/xfce-perchannel-xml/thunar.xml \
	~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-desktop.xml \
	~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml \
	~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-notifyd.xml \
	~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml \
	~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-screensaver.xml \
	~/.config/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml
	...
```

## Remove unneeded components

```sh
sudo pacman -Rns \
	xfce4-dict \
	xfce4-terminal \
	xfce4-screenshooter \
	xfce4-clipman-plugin \
	ristretto
	# xfce4-notifyd
	# xfwm4
```

[^1]: [Install XFCE Desktop on Arch Linux](https://linuxopsys.com/topics/install-xfce-desktop-on-arch-linux)
[^2]: [Install a Nerd Font](https://www.lunarvim.org/docs/installation/post-install#install-a-nerd-font)