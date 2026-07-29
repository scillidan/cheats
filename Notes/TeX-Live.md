## Install on Arch[^1][^2]

```sh
yay -S --noconfirm texlive-installer
```

```sh
sudo /opt/texlive-installer/install-tl
sudo /usr/local/texlive/2024/bin/x86_64-linux/tlmgr option repository https://mirrors.cernet.edu.cn/CTAN/systems/texlive/tlnet
tlmgr update --list
sudo /usr/local/texlive/2024/bin/x86_64-linux/tlmgr update --all
# tlmgr search --global <pkg>
```

## Upgrade from 2024 to 2025[^3]

```sh
sudo cp -a /usr/local/texlive/2024 /usr/local/texlive/2025
cd /usr/local/texlive/2025
sudo wget https://mirror.ctan.org/systems/texlive/tlnet/update-tlmgr-latest.sh
sudo PATH=$PATH ./update-tlmgr-latest.sh -- --upgrade texlive/2025
sudo /usr/local/texlive/2025/bin/x86_64-linux/tlmgr option repository https://mirrors.cernet.edu.cn/CTAN/systems/texlive/tlnet
sudo /usr/local/texlive/2025/bin/x86_64-linux/tlmgr update --self --all
luaotfload-tool -fu
```

```sh
pdflatex --shell-escape "$1"
```

[^1]: [TeX Live](https://wiki.archlinux.org/title/TeX_Live)
[^2]: [tlmgr](https://tug.org/texlive/doc/tlmgr.html)
[^3]: [Upgrade from TeX Live 2024 to 2025](https://www.tug.org/texlive/upgrade.html)