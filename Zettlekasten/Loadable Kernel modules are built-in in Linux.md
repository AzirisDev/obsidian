The .ko files/loadable kernel modules are object files that will be downloaded when driver is needed.

- located in /lib/modules
- lsmod - check modules available
- rmmod "module name" - remove module
- modprobe "module name" - add module

If we need to stay modules consistent even after reboot, we need to take a look at the /etc/modules and /etc/modprobe.d files.

Links:

202509041710

