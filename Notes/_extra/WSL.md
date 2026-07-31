---
tags: windows
---

## Install[^1][^2][^3]

```pwsh
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
DISM /Online /Enable-Feature /All /FeatureName:Microsoft-Hyper-V
```

```sh
wsl --set-default-version 2
wsl --update --web-download
wsl --list --online
wsl --install <distro>
```

## Optional

### Remove Windows 10's PATH[^4][^5]

```sh
sudo vim /etc/wsl.config
```

```
[interop]
appendWindowsPath = false
```

### [WSLg](https://github.com/microsoft/wslg)

Turn on[^6]\:

```sh
ln -s /mnt/wslg/runtime-dir/wayland-0* /run/user/1000/
```

Turn off[^7]\:

```sh
subl %UserProfile%\.wslconfig
```

```
[wsl2]
guiApplications=false
```

[^1]: [Install Hyper-V](https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/get-started/Install-Hyper-V?pivots=windows)
[^2]: [How to install Arch Linux for WSL](https://dev.to/jrcharney/how-to-install-arch-linux-for-wsl-184a)
[^3]: [WSL --update fails with unknown error code (0x80240066)](https://github.com/microsoft/WSL/issues/9039)
[^4]: [How to remove the Win10's PATH from WSL](https://stackoverflow.com/questions/51336147/how-to-remove-the-win10s-path-from-wsl)
[^5]: [[Question] How to remove Windows pathes from WSL PATH?](https://github.com/microsoft/WSL/issues/1493#issuecomment-266480323)
[^6]: [GUI Applications will no longer launch in Wayland after updating](https://github.com/microsoft/wslg/issues/1032)
[^7]: [Disable WSLg permanently](https://github.com/microsoft/wslg/discussions/523)