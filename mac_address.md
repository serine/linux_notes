## Spoofing mac address for ethercard 

#### Temporal change (until reboot or service restart)

- `ifconfig eth0 down`
- `ifconfig eth0 hw ether 08:00:00:00:00:01`
- `ifconfig eth0 up`

#### Permanent change

- make `systemd` service file `/etc/systemd/system/check-macaddr.service`
- append something like this into it, note that you want this service to run before `dhcp` service

```BASH
[Unit]
Description=check mac address
Before=network.target

[Service]
ExecStart=/usr/local/bin/check-macaddr.sh

[Install]
WantedBy=default.target
```

- change permissions `chmod 664 /etc/systemd/system/check-macaddr.service`

- make script with the same name as your service `/usr/local/bin/check-macaddr.sh`
- append something like this into it, this script will be run during boot process

```BASH
#!/bin/sh

ifconfig eth0 donw
ifconfig eth0 hw ether 78:2b:cb:87:75:15  
ifconfig eth0 up
```
- change permissions `chmod 744 /usr/local/bin/check-macaddr.sh`

## Reference

- [ArchLinux](https://wiki.archlinux.org/index.php/MAC_address_spoofing)
