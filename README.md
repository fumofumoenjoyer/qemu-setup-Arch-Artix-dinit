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
## Systemd (Arch)
```
sudo systemctl enable libvirtd
sudo systemctl enable virtqemud
sudo systemctl enable virtxend
sudo systemctl enable virtlxcd
sudo systemctl enable virtbhyved
sudo systemctl enable virtvboxd
sudo systemctl enable virtinterfaced
sudo systemctl enable virtnetworkd
sudo systemctl enable virtnodedevd
sudo systemctl enable virtnwfilterd
sudo systemctl enable virtsecretd
sudo systemctl enable virtstoraged
```
## dinit (Artix) (BROKEN)
```
sudo dinitctl enable libvirtd
```

## Reboot and open virtmanager to manage your VMs
