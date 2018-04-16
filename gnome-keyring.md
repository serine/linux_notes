## Disable gnome-keyring

No particular reason, but don't want to use `gnome-keyring`
Preferably I'd want to `apt-get remove gnome-keyring`, but when I tried,
it prompts to remove the whole `gnome-desktop` and bunch of other central 
packages. 

From memory `gnome-keyring` had some unwanted behaviour with ssh keys forwarding..

There are a bunch of different `gnome-keyring-*` files at that location

```
cd /etc/xdg/autostart
X-GNOME-Autostart-enabled=false
```

I edited them all and added line above

```
[biostation2]~$ ls -1 /etc/xdg/autostart/gnome-keyring-*
/etc/xdg/autostart/gnome-keyring-pkcs11.desktop
/etc/xdg/autostart/gnome-keyring-secrets.desktop
/etc/xdg/autostart/gnome-keyring-ssh.desktop
```
