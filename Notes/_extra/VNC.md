## On Arch[^1][^2][^3][^4]

```sh
vncpasswd
# A view-only password is not used → No
```

```sh
sudo useradd -m vncuser
sudo passwd vncuser
sudo vim /etc/tigervnc/vncserver.users
```

```
:1=vncuser
```

```sh
# rm -rf ~/.vnc
# mkdir ~/.vnc
vim ~/.vnc/config
```

```
# session=xfce
geometry=1280x720
# localhost
alwaysshared
```

```sh
# vncserver :1
# sudo systemctl enable --now vncserver@:1
vim ~/vncstart.sh
```

```sh
#!/bin/bash
vncserver -kill :1 > /dev/null 2>&1
rm -f /tmp/.X1-lock
rm -f /tmp/.X11-unix/X1
vncserver :1
```

```sh
chmod u+x ~/vncstart.sh
```

```sh
./vncstart.sh
```

[^1]: [Setting up tigervncserver on arch linux (raspberry-pi)](https://rushichaudhari.github.io/posts/2020-10-29-setting-up-tigervncserver-on-arch-linux-raspberry-pi/)
[^2]: [TigerVNC Server in Manjaro (Arch Linux) - Headless Guide 2021!](https://www.youtube.com/watch?v=w1HS_xVnFFo)
[^3]: [How to Install & Configure VNC Server on Ubuntu 22.04](https://bytexd.com/how-to-install-configure-vnc-server-on-ubuntu/)
[^4]: [Using Graphical User Interface in WSL](https://hackmd.io/@heymosbrother/ryQS8PWa9)