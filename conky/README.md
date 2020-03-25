# How to install conky for Raspberry Pi
### Based on:
https://www.novaspirit.com/2017/02/23/desktop-widget-raspberry-pi-using-conky/

# Install conky
sudo apt-get install conky -y
# Set configuration file 
Copy .conkyrc to your folder `/home/pi/.conkyrc`
# Create autorun scripts
Create shell script:

`sudo nano /usr/bin/conky.sh`

And paste

```shell
#!/bin/sh
(sleep 4s && conky) &
exit 0
```

Create the conky.desktop file for the autostart process

`sudo nano /etc/xdg/autostart/conky.desktop`

And paste

```
[Desktop Entry]
Name=conky
Type=Application
Exec=sh /usr/bin/conky.sh
Terminal=false
Comment=system monitoring tool.
Categories=Utility;
```

Reboot - everything should work nicely!