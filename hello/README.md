# A hello world linux driver 

This is a directory for a simple kernel driver. All this driver needs to do is say "hello world" when inserted into the kernel with insmod and goodbye when removed with rmmod.

## Building the module_exit
To build this module against the installed kernel in your system, open a terminal and cd into this directory in the repo. Then call make:
	make 
	make -C /lib/modules/version/build M=/home/me/src/linux-kernel-drivers/hello modules
	make[1]: Entering directory '/usr/src/linux-headers-version'
	CC [M]  /home/muriuki/src/linux-kernel-drivers/hello/hello.o
	Building modules, stage 2.
	MODPOST 1 modules
	CC      /home/me/src/linux-kernel-drivers/hello/hello.mod.o
	LD [M]  /home/me/src/linux-kernel-drivers/hello/hello.ko
	make[1]: Leaving directory '/usr/src/linux-headers-version'

## Testing the module
To test the kernel module, the test makefile target is used. It clears dmesg, loads the module in the kernel, unloads the module and prints the contents from dmesg during this two actions.
	sudo dmesg -C
	sudo insmod hello.ko
	sudo rmmod hello.ko
	dmesg
	[ 1680.811315] hello world
	[ 1680.817882] goodbye
