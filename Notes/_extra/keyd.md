---
tags: arch
---

```sh
sudo pacman -S keyd
```

```sh
sudo systemctl enable keyd --now
sudo vim /etc/keyd/default.conf
# Copy from https://github.com/rvaiya/keyd?tab=readme-ov-file#recommended-config
```

```
[ids]

*

[main]

# shift = oneshot(shift)
# meta = oneshot(meta)
# control = oneshot(control)
# leftalt = oneshot(alt)
# rightalt = oneshot(altgr)
capslock = overload(control, esc)
insert = S-insert
```

```sh
sudo keyd reload
```