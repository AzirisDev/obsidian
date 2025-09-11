VM is software simulations of a computer. We need Hypervisor as VirtualBox or UTM to create and run VMs. We can check for flags `vmx` (Intel) or `svm` (AMD) to know that the machine is virtualized.

#### There are two types of Hypervisors
- Hosted: hardware -> host OS -> hypervisor -> guest OS
- Native: hardware -> hypervisor -> guest OS

#### Creating VMs and vital details
We can install it via ISO file, clone existing one, use Open Virtualized Format or Open Vritualized Archive to be imported.

It is vital to check hostname, MAC address, machine id, hard disk uuid to avoid clashes around VMs.


### VMS vs Containers

- VM: Hardware -> (Host OS) -> Hypervisor -> Guest OS -> Libraries -> Apps
- Containers: Hardware -> Host OS -> Container Engine -> Binaries/Libraries -> Apps
Containers **do not need** a separate OS.

#### IaaS
These are cloud platforms like Amazon Web Services, Google Gloud Platform, Microsoft Azure. They provide virtualized computing infrastructure as power, networking, storage and databases.
- cloud-init - A command-line tool that helps **initialize cloud instances** with configurations



Links: [[Linux virtual machine]] 

202509110956

