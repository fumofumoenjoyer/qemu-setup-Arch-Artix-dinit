# qemu-setup-Arch-Artix-dinit
## Install packages
```
sudo pacman -Syyu dnsmasq virt-manager qemu-full libvirt
```
## For Artix also install the respective service.
I use dinit, but there should be a package for your init system.
```
sudo pacman -S libvirt-dinit
```
## Edit files
Edit ```/etc/libvirt/libvirtd.conf``` (Uncomment the following Lines)
```
unix_sock_group = "libvirt"
unix_sock_rw_perms = "0770"

```
Then add your user and create group:
```
sudo usermod -a -G libvirt $(whoami)
newgrp libvirt

```

## Enable Services
## Systemd
```
sudo systemctl enable libvirtd
```
## dinit
```
sudo dinitctl enable libvirtd
```

## Reboot and done
