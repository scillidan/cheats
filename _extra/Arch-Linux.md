Preparations:

- [了解 archlinux](https://arch.icekylin.online/guide/prepare/understand.html)
- (Optional) [安装前的准备](https://arch.icekylin.online/guide/rookie/pre-install.html)

[^1]

```sh
systemctl stop reflector.service
```

```sh
timedatectl set-ntp true
```

```sh
cp /etc/pacman.d/mirrorlist /etc/pacman.d/mirrorlist.bak
vim /etc/pacman.d/mirrorlist
```

```
Server = https://mirrors.ustc.edu.cn/archlinux/$repo/os/$arch
```

```sh
lsblk
cfdisk /dev/nvme?n1
```

```
size        | type             | comment
1G          | EFI System       | /boot
32G*0.6=18G | Linux Swap       |
free        | Linux filesystem | /
```

```sh
mkfs.fat -F32 /dev/nvme?n1p1
mkswap /dev/nvme?n1p2
mkfs.btrfs -L Arch /dev/nvme?n1p3
```

```sh
mount -t btrfs -o compress=zstd /dev/nvme?n1p3 /mnt
btrfs subvolume create /mnt/@
btrfs subvolume create /mnt/@home
btrfs subvolume list -p /mnt
umount /mnt
```

```sh
mount -t btrfs -o subvol=/@,compress=zstd /dev/nvme?n1p3 /mnt
mkdir -p /mnt/home
mount -t btrfs -o subvol=/@home,compress=zstd /dev/nvme?n1p3 /mnt/home
mkdir -p /mnt/boot
# Mount EFI
mount /dev/nvme?n1p1 /mnt/boot
# Mount Linux Swap
swapon /dev/nvme?n1p2
```

```sh
pacstrap /mnt base base-devel linux linux-firmware btrfs-progs
```

```sh
pacstrap /mnt networkmanager vim sudo zsh zsh-completions
```

```sh
genfstab -U /mnt > /mnt/etc/fstab
```

```sh
arch-chroot /mnt
```

[^2]

```sh
vim /etc/hostname
```

```
arch
```

```sh
vim /etc/hosts
```

```
# Add
127.0.1.1	arch.local arch
```

[^3]

```sh
# timedatectl set-timezone Asia/Shanghai
ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
hwclock --systohc
```

[^4][^5]

```sh
vim /etc/locale.gen
```

```
# Find and uncomment
en_US.UTF-8 UTF-8
zh_CN.UTF-8 UTF-8
```

```sh
locale-gen
```

```sh
vim /etc/locale.conf
```

```
LANG=en_US.UTF-8
```

```sh
passwd root
```

```sh
useradd -m -G wheel -s /bin/bash <user>
passwd <user>
EDITOR=vim visudo
```

```
# Uncomment
%wheel ALL=(ALL:ALL) ALL
```

```sh
# AMD CPU
pacman -S amd-ucode
# AMD GPU
sudo pacman -S mesa lib32-mesa vulkan-radeon lib32-vulkan-radeon
# Intel CPU
pacman -S intel-ucode
# NVIDIA GPU
sudo pacman -Syu linux-headers
sudo pacman -S nvidia nvidia-utils nvidia-settings nvidia-dkms
sudo mkinitcpio -P
sudo modprobe nvidia
```

```sh
pacman -S grub efibootmgr os-prober
grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=ARCH
vim /etc/default/grub
```

```
GRUB_CMDLINE_LINUX_DEFAULT="loglevel=5 nowatchdog"
```

```sh
grub-mkconfig -o /boot/grub/grub.cfg
```

```sh
exit
umount -R /mnt
shutdown -h now
sudo systemctl enable --now NetworkManager
```

[^6]

```sh
lsblk -o name,mountpoint,size,uuid
# Get UUID of Swap Partition
sudo vim /etc/default/grub
```

```
GRUB_CMDLINE_LINUX_DEFAULT="loglevel=5 nowatchdog resume=UUID=<swap_uuid>"
```

```sh
sudo grub-mkconfig -o /boot/grub/grub.cfg
sudo vim /etc/mkinitcpio.conf
```

```
HOOKS=(base udev resume ...)
```

```sh
sudo mkinitcpio -P
sudo reboot
```

## Cross reference

1. [[ArchWSL]]
2. [[Pacman]]
3. [[yay]]
4. [[Flatpak]]
5. [[OpenSSH]]
6. [[VNC]]
7. [[firewalld]]
8. [[BlueZ]]
9. [[Mount]]

## Troubleshoot

### Bluetooth service was skipped because of an unmet condition check ...[^7]

```sh
sudo modprobe bluetooth
sudo systemctl restart bluetooth
systemctl status bluetooth
```

[^1]: [archlinux 基础安装](https://arch.icekylin.online/guide/rookie/basic-install)
[^2]: [Set the hostname](https://wiki.archlinux.org/title/Network_configuration#Set_the_hostname)
[^3]: [System time](https://wiki.archlinux.org/title/System_time)
[^4]: [Localization](https://wiki.archlinux.org/title/Localization)
[^5]: [Localization/Simplified Chinese](https://wiki.archlinux.org/title/Localization/Simplified_Chinese)
[^6]: [可选配置（进阶篇）- 休眠（hibernate）设置](https://arch.icekylin.online/guide/advanced/optional-cfg-2.html#%F0%9F%92%A4-%E4%BC%91%E7%9C%A0-hibernate-%E8%AE%BE%E7%BD%AE)
[^7]: [Bluetooth not working on computer](https://www.linuxquestions.org/questions/linux-hardware-18/bluetooth-not-working-on-computer-4175724971/)