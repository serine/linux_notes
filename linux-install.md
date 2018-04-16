# Installing linux

## Debian flavour

- download debian image e.g `debian-9.4.0-amd64-netinst.iso`
- insert and unmount your USB stick.

```
lsblk
umount /dev/sdb1
```
 
- burn iso image to USB

```
dd bs=4M if=ubuntu-12.04.2-server-i386.iso of=/dev/sdb
```

- to make FAT32 filesystem back on USB key

```
mkdosfs -F 32 -n usbkee -I /dev/sdb 
```

## command not found

- ifconfig
- iwconfig
- sudo
- less

## apt-get

- `sudo`
- `less`
- `gcc`
- `make`

- `firmware-linux-nonfree`

## kernel compiling

- `bison`
- `flex`


