## How to create an autostart

```
mkdir ~/.config/autostart
vim ~/.config/autostart/chrome.desktop
```

and append these lines to `chrome.desktop` file

```
[Desktop Entry]
Type=Application
Exec=/usr/bin/google-chrome
Hidden=false
X-GNOME-Autostart-enabled=true
Name=pidgin
Comment=google-chrome
```

Next time you reboot chrome will automatically start

## Other

Usually desktop files are located here

```
/usr/share/applications/*.desktop
```

## References

- [askubutu](https://askubuntu.com/questions/37957/how-do-i-manage-applications-on-startup-in-gnome-3)
