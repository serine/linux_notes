# /etc/init

There are at least three systems in debian family (mainly) that start, stop and handle tasks and services on the startup, shutdown.

- [SysV](https://www.cyberciti.biz/tips/linux-write-sys-v-init-script-to-start-stop-service.html)
- [Upstart](http://upstart.ubuntu.com/index.html)
- [systemd](https://wiki.debian.org/systemd)

Most currently used is systemd, although you can still find SysV installed for backward compatability? I think. 

- `/etc/init.d` -> `SysV`
- `/etc/init/` -> `upstart` and `systemd`

I understand that `systemd` superseded `upstart`

- `man init` for more info

