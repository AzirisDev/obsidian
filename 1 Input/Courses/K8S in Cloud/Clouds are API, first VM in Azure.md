In azure, we create `subscription` and inside it we are going to have `resource groups`. `Subscription` is a logical container that contains all resources that we create and controls billing, access and limits.

Lets create VM.

1) Select/create `resource group`
2) Choose region - more convenient for us is West Europe
3) We can choose `availability zone` to separate physically resources and increase resilience of applications
4) Keep everything simple, choose standard `security`
5) `Size` also keep minimal with 1Gb Memory
6) Generate `ssh` key pair
7) Disk size 30Gb, choose type standard SSD for economy sake
8) Check the box `Delete with VM` cause we need to delete memory with VM, so bills do not hit us
9)  Networking with default values
10) Management - check `Enabling free plan`
11) Other stuff is default values

Actually we just fill out `json` file for Azure API just like we did with `yaml` files for kubernetes API to deploy anything.

Azure creates not only VM, but many other things in `resource group`. `NetworkWatcherRG` - it's Azure's network monitoring and diagnostics service.  In `test01` resource group we have: `vnet` - virtual network - private IP address range; `network interface` - network card to connect to network; etc.

Links:

202611181133

