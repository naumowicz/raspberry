# How to setup Resilio Sync for file synchronization and backup
## What's needed
- Main PC
- Drive for Raspberry
- Raspberry
- LAN connection between PC and Raspberry

# Auto mount your drive

## Based on:
https://www.linuxbabe.com/desktop-linux/how-to-automount-file-systems-on-linux

# Step 1: Get the Name, UUID and File System Type

Use command `sudo blkid`

# Step 2: Make a Mount Point For Your Drive

We are going to make a mount point under /home/pi/usb directory. Enter the following command:

sudo mkdir `/home/pi/usb `

# Step 3: Edit /etc/fstab File

`sudo nano /etc/fstab`

We need to append one line of code at the end of the file. The format of this line of code is as follows:

`PARTUUID=<uuid-of-your-drive>  <mount-point>  <file-system-type>  <mount-option>  <dump>  <pass>`

As a example:

`PARTUUID=eb67c479-962f-4bcc-b3fe-cefaf908f01e  /mnt/sdb9  ntfs  defaults  0  2`

**Note that Raspberry's OS - Raspbian uses PARTUUID but Linux uses UUID**

# Step 4: Reboot Raspberry Pi
Everything should work as expected.

You can find more info about fstab here: https://en.wikipedia.org/wiki/Fstab

# Time to install Resilio service

## Based on:

https://help.resilio.com/hc/en-us/articles/206178924-Installing-Sync-package-on-Linux

# Download or install packege from repository

Follow instruction for Linux (Debian), not puslishing how it's done because manual can change after some time.

From my experience I advide starting Resilio service from Pi user:

`systemctl --user enable resilio-sync`

To start service as Pi:

`systemctl --user start resilio-sync`

Service can be restarted, stopped and started.

Use: `start, stop, restart`:

`sudo service resilio-sync start`

# Connect peers

It's easiest part (do it yourself, your way).

# Synchonize

Everything should work as expected, peers should communicate and sync files.

Raspberry service runs as web application under `localhost:8888/gui/`