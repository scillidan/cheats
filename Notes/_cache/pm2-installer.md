---
tags: windows
---

## On Windows 10[^1]

```sh
git clone --depth=1 https://github.com/jessety/pm2-installer
cd pm2-installer
sudo npm run configure
sudo npm run setup
sudo pm2 save
```

Windows 10 → Control Panel → Administrative Tools > Services → PM2 → Properties → Log On → local system account → Go back to first tab → Start[^1].

[^1]: [State is now: Stopped](https://github.com/jessety/pm2-installer/issues/69)