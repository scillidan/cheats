---
tags: arch
---

```sh
sudo vim /etc/hosts
```

```
<ip>	github.com
<ip>	raw.githubusercontent.com
```

```sh
sudo systemctl restart systemd-resolved
```

[^1]: [hosts](https://man.archlinux.org/man/hosts.5)