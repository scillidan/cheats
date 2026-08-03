```sh
sudo pacman -S qemu virt-manager virt-viewer dnsmasq vde2 bridge-utils openbsd-netcat
sudo pacman -S dmidecode
```

## usage[^1]

```sh
sudo systemctl enable --now libvirtd
systemctl status libvirtd
sudo usermod -aG libvirt,kvm $(whoami)
```

```sh
grep kvm
sudo modprobe kvm
# AMD
sudo modprobe kvm_amd
# AMD
echo -e "kvm\nkvm_amd" | sudo tee /etc/modules-load.d/kvm.conf
```

```sh
virsh net-list --all
sudo virsh net-autostart default
sudo virsh net-start default
```

- QEMU/KVM → Add
 	1. Choose how you would like to install the operating system → Manual install.
 	2. Choose the operating system you are installing → `Microsoft Windows 10`.
 	3. Create a disk image for the virtual machine → `100G`.
 	4. Ready to begin the installtion → Name → `Win10`.

```sh
sudo qemu-system-x86_64 \
  -enable-kvm \
  -m 2048 \
  -cpu host \
  -smp 2 \
  -cdrom <path_to>/windows10_x64_cn.iso \
  -boot d \
  -drive file=/var/lib/libvirt/images/win10.qcow2,format=qcow2 \
  -net nic -net user \
  -name "windows10 VM"
```

- TigerVNC viewer → VNC server → `localhost:5900` → Connect.

[^1]: [How to Install and Use QEMU/KVM on Arch Linux | Siberoloji](https://www.siberoloji.com/how-to-install-and-use-qemukvm-on-arch-linux/)