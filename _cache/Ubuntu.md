```sh
sudo apt update
sudo apt upgrade -y
# sudo apt-get clean
# sudo apt-get autoremove
```

```sh
timedatectl set-timezone Asia/Shanghai
```

## Use repository mirror[^1]

```sh
mkdir -p /etc/apt/sources.list.d
sudo cp /etc/apt/sources.list.d/ubuntu.sources /etc/apt/sources.list.d/ubuntu.sources.bak
sudo vim /etc/apt/sources.list.d/ubuntu.sources
```

```
# Ubuntu 22 ARM
Types: deb
URIs: https://mirrors.ustc.edu.cn/ubuntu-ports
Suites: jammy jammy-updates jammy-backports
Components: main restricted universe multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg

Types: deb
URIs: https://mirrors.ustc.edu.cn/ubuntu-ports
Suites: jammy-security
Components: main universe restricted multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
```

```
# Ubuntu 24 ARM
Types: deb
URIs: https://mirrors.ustc.edu.cn/ubuntu-ports
Suites: noble noble-updates noble-backports
Components: main restricted universe multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg

Types: deb
URIs: https://mirrors.ustc.edu.cn/ubuntu-ports
Suites: noble-security
Components: main universe restricted multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
```

```sh
sudo apt update
```

[^1]: [USTC Mirror Help - Ubuntu](https://mirrors.ustc.edu.cn/help/ubuntu.html)