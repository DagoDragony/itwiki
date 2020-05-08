# Remote Connection

## Vnc

```
sudo pacman -S x11vnc

x11vnc --storepasswd /home/dago/.vnc/passwd # password for connection (vnc server part)
```

```
# if you would add vnc start in your desktop manager initialization script,
# you will need only to turn on computer to log in to it
# for mdm it's in /etc/mdm/Init/Default add line bellow before exit 0
/usr/bin/x11vnc -shared -forever -nodpms -noxdamage -rfbport 5900 -display :0 -o /var/log/x11vnc.log -rfbauth /home/dago/.vnc/passwd
```

### For raspberry pi `sudo nano /etc/rc.local`

```
/usr/bin/x11vnc -shared -forever -nodpms -noxdamage -rfbport 5900 -display :0 -auth /var/run/lightdm/root/:0 -userpw &
sudo nano /etc/rc.local
```
