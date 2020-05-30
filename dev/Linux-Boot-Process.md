# Linux Boot Process

## Hardware boot

* BIOS - Basic I/O system(newer UEFI (User Extendable Firmware Interface)
	* POST (power on self test)
		* Checks basic operability of the hardware
		* Locates boot sectors on all attached bootable devices
	* First valid MBR is loaded into RAM and control is then transferred to the
	  RAM copy of the boot sector

## Linux boot

* GRUB (GRand Unified Bootloader) - 
	* First part of GRUB is loaded into RAM
	  MBR 512b sector in first partition is executed
	  `/boot/grub/i386-pc/boot.img`
	* Second part of GRUB is loaded into RAM
	  In MBR gap or boot track - space between MBR (sector 1 of 512b to sector 63 - where first partition starts)
	  Function - begin execution with filesystem drivers necessary to locate next stage and load the needed drivers
	  `/boot/grub/i386-pc/core.img`
	* Locate and load a Linux kernel into RAM and turn control of the pc over to the kernel
	  Consists of files and runtime kernel modules that are loaded as needed from the `/boot`
	  Shows preboot selection screen
	  All kernel files are identifyable by start of `vmlinuz`
* Kernel 
	* Extract itself(after it is loaded to RAM by GRUB) 
	* Load SystemD
	* SystemD startup
		* Mount `/etc/fstab`
		* etc...
		* Desktop Manager
		* Windows Manager

Login
1. systemd starts systemd-getty-generator daemon
2. systemd-getty-generator spawns an agetty on each of the virtual consoles using the serial-getty@.service
3. agettys wait for virtual console connection, which is the user switching to on of the VCs
4. aggetty presents the text mode login screen on the display
5. the user logs in
6. the shell specified in /etc/passwd is started
7. shell configuration scripts run
8. the user works in the shell session
9. the user logs off
10. the systemd-getty-generator spawns an agetty on the logged out on VC
11. go to step step 3
