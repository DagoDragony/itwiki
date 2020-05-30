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
	* MBR 512b sector(boot.img) is executed GRUB is loaded into RAM
