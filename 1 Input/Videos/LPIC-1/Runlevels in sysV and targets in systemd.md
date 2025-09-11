Runlevels or boot targets are like stages of being alive of the system in sysV and systemd, respectively.

- systemctl get-default -> shows current running target
- runlevel -> shows current runlevel
- systemctl cat name.target -> get info about the target
- systemctl isolate name.target -> move to specific targets
	- rescue - local file systems are mounted, no network, only root user - maintenance mode
	- emergency - root file systems are available, read-only, no network, only root user - maintenance mode
	- reboot
	- halt - stops every CPU activity
	- poweroff - turns everything off
- telinit № of level - runs specific run level
	- Red Hat systems levels:
		- 0- Shutdown
		- 1- Single-user mode; Also called S or s, can be passed as arguments while boot
		- 2- Multi-user without networking
		- 3- Multi-user with networking
		- 4- to be customized by the admin
		- 5- Multi-user with networking and graphics
		- 6- Reboot
	- Debian system levels:
		- 0- Shutdown
		- 1- Single-user mode
		- 2- Multi-user mode with graphics
		- 6- Reboot

[[Stop and inform users about shutdown]]

