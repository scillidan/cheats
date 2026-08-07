---
tags: config
---

## On Ubuntu ARM[^1]

```sh
sudo apt install mono-devel
```

Get `Jackett.Binaries.LinuxARM64.tar.gz` from [Releases](https://github.com/Jackett/Jackett/releases).

```sh
tar -xvzf Jackett.Binaries.LinuxARM64.tar.gz
cd Jackett
./jackett_launcher.sh
# Exit
```

```sh
sudo ./install_service_systemd.sh
sudo systemctl status jackett.service
```

## Config

- Jackett → Configured Indexers → Add Indexer
	- Torrents.csv (Add)
	- Knaben (Add)
	- TheRARBG (Add)

[^1]: [How to Install Jackett on Ubuntu 20.04](https://varhowto.com/install-jackett-ubuntu-20-04/)