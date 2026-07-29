---
tags: arch
---

## Install[^1]

```sh
sudo pacman -S openssh
```

```sh
sudo systemctl enable --now sshd
# sudo ufw allow 22/tcp
# ip addr show
```

## Enable Pubkey Authentication

```sh
sudo vim /etc/ssh/sshd_config
```

```
PubkeyAuthentication yes
# AuthorizedKeysFile ...
PasswordAuthentication no
```

```sh
sudo systemctl restart sshd
```

```sh
ssh-keygen -t rsa -b 2048 -f ~/.ssh/id_rsa
# Copy from ~/.ssh/id_rsa.pub
```

## On client PC

```sh
mkdir ~/.ssh
vim ~/.ssh/authorized_keys
vim ~/.ssh/authorized_keys2
# Paste into
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys*
```

[^1]: [enable SSH on Arch Linux](https://medium.com/@pythonaugust/enable-ssh-on-arch-linux-8f1ede0d9c88)