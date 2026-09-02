Before containerization era we have problems in both development and deployment of the software:
- "it works on my machine" problem
- Dependency hell
- Mac vs Linux vs Windows incompatibility
- Installation of right runtime and libraries versions

Containers solved it:
- setup and run everywhere
- it became -> "it works in my container"
### Virtualization Evolution

1) **Bare metal** - all application runs on one machine.
	- underutilization o full hardware -> 64-core 
	- one and connected point of failure
	- minutes to boot hardware server
2) **Virtual machines** - improvement; no we have `hypervisor` to create and control separate  VMs with their own OS.
	- memory overhead - each OS weighs a lot
	- heavy resource usage
3) **Containers** - they share host OS kernel. Great improvement.
	- less isolation - if not properly configured
	- Linux containers run only on Linux machines

Links:

202608312048

