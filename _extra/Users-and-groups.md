---
tags: arch
---

```sh
# Add user
sudo useradd -m <user>
sudo passwd <user>
```
```sh
# Add group
sudo addgroup sudousers
```

```sh
# Add user into group
sudo usermod -aG sudousers <user>
```

```sh
# Remove user from group
sudo gpasswd -d <user> <group>
```