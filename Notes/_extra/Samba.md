## On Ubuntu 22 ARM[^1][^2]

```sh
sudo apt install samba
```

```sh
sudo useradd -m smbuser
sudo smbpasswd -a smbuser
sudo groupadd -r smbusers
sudo usermod -aG smbusers smbuser
sudo chown smbuser:smbusers <path_to>/<share_name>
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
sudo vim /etc/samba/smb.conf
```

```
workgroup = <SMBGPNAME>
# interfaces = <wired_interfaces> <wireless_interfaces>

[<share_name>]
comment = Share Name
path = <path_to>/<share_name>
guest ok = no
read only = no
browsable = yes
writable = yes
create mask = 0644
directory mask = 2755
# force create mode = 0664
# force directory mode = 2775
# force group = smbusers
```

```sh
sudo systemctl restart smbd
```

## On Arch

```sh
sudo pacman -S samba
sudo vim /etc/samba/smb.conf
# https://git.samba.org/samba.git/?p=samba.git;a=blob_plain;f=examples/smb.conf.default;hb=HEAD
sudo smbpasswd -a smbuser
```

```sh
sudo systemctl start smb nmb
sudo systemctl enable smb nmb
```

## Client on Windows 10

1. Windows 10 → 计算机管理 → 本地用户和组 → 用户 → 右键 → 新用户:
   - 用户名 → smbuser
   - 用户不能更改密码 (On)
   - 密码永不过期 (On)
2. 本地用户和组 → 组 → 右键 → 新建组 → 组名 `SMBGPNAME` → 添加 → 输入对象名称来选择 `smbuser` → 确认 → 创建.
3. 资源管理器 → 此电脑 → 右键 → 添加一个网络位置 → 指定网站的位置 → `\\<your_host>\<path_to_share>` → 请键入该网络位置的名称 `<any_name>`.
4. 网络位置 → `\\<your_host>\<path_to_share>` → 右键 → 映射网络驱动器 → 登录时重新连接 On → 完成.

[^1]: [Installing and Configuring Samba on Ubuntu 22](https://reintech.io/blog/installing-configuring-samba-ubuntu-22)
[^2]: [Implementing Samba on Arch Linux: A Comprehensive Guide](https://shape.host/resources/implementing-samba-on-arch-linux-a-comprehensive-guide)
