## Peripheral Component Interconnect (PCI)

> is a local computer bus for attaching hardware devices in a computer

### Typical PCI cards used in PCs:

- network card
- sound card
- modems

In computer architecture a **bus** is a communication system that transfers data between components inside a computer or between computers. 

A microprocessor conventionally is single chip which has a number of electrical connections on its pins that can be used to select an "address" in the main memory and another set of pins to read and write the data sotred at the location. 

Cache is memory that is built-in directly into CPU

Memory address is a data concept used at various levels by sofware and hardware to access the computers primary storage memory. Memory address are fixed-length sequences of digits conventionally displayed and manipulated as unsigned intergers.

`dmidecode` use this command to get info about your hardware

## Working with video drivers

- `lspci -v` gives veborse description of each pci device
- `lspci | grep -i vga` to quickly grab video controller

- `lshw -class display` outputs information about video controller

- `find /dev -group video` don't understand the output yet

- `/usr/lib/nux/unity_support_test -p` to test unity3D

## 

To get informatiom about actual chip installed
```
grep -i chipset /var/log/Xorg.0.log 
```

Mine is 

```
[     4.337] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
[     4.337] (II) VESA: driver for VESA chipsets: vesa
[     4.339] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4400
```

I've downloaded latest-stable intel graphics drivers from intel, it's just the matter of installing

This kernel with Intel drivers seems to work well - fast

```
Linux version 4.4.0-47-generic (buildd@lcy01-03) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.2) ) #68-Ubuntu SMP Wed Oct 26 19:39:52 UTC 2016
```

## 2016.12.8

added code below into `/etc/X11/xorg.conf`. That file didn't exist before. 

```
Section "Device"
    Identifier  "Intel Graphics"
    Driver      "intel"
    Option      "AccelMethod"  "uxa"
EndSection
```

I'm not sure if this is doing anything, should read mroe about what it does

https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-16.04-Enable-DRI3

## 

evince --version
google-chrome --version
libreoffice --version
convert --version
ubuntu-drivers devices

## 

- It is possible that I have two chipsets (GPUs) that one for internal screen and other for external. Need to find out how do I have

- Possible that one chipset, but the driver has some issues 

- Possible that cpu struggles to drive high res pixles resolution

##

lspci -kvnn
modinfo i915
modinfo i915 | grep filename
bash -c modinfo i915 | (read x path && dpkg -S $path)
