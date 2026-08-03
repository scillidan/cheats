- Raspberry Pi Imager
	1. Raspberry Pi Device → Choose Device → `Raspberry Pi 4`
	2. Operating System → Choose OS → Other general-purpose OS → Ubuntu → `Ubuntu Server 22.04.4 LTS (64-bit)`
	3. Storage → Choose Storage → `<your_sdcard>`
	4. Next → Edit settings
    - General
	    - Set hostname → `ubuntu22`
	    - Set username and password
	    	- Username → `<user>`
	    	- Password → `<password>`
	    - Configure wireless LAN
	    	- SSID → `<your_wifi>`
	    	- Password → `<wifi_password>`
	    - Wireless LAN country → `CN`
	  	- Set locale settings
	  		- Time zone → `Asia/Shanghai`
	  		- Keyboard layout → `us`
    - Services → Enable SSH (On) → Use password authentication
    - Options
    	- Eject media when finished (On)
    	- Enable telemetry (Off)