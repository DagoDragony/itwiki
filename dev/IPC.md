# IPC 

Inter Process Communication 

## D-BUS

From 2006
System-wide and more complex form of IPC that allows many kernel- and system-level process
to send messages

## udev

Daemon for devices
* Creates `/dev` device files only for devices that actually currently exist OR have a high
  probability of actually existing on the host
* Assigns names to devices when they are plugged. udev treats all devices as plug & play
  even on boot. udev moves device naming out of kernel space into user space
