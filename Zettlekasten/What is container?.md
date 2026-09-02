`Container image` - blueprint containing everything you need to run the application: dependencies, runtime, base OS libraries
`Container` - running instance of Container image.

### Linux containers
They are built-in Linux kernel features. We use two things to make it happens: namespaces(isolation) and cgroups(limit resources).
Docker - is one of the tools that makes it easy to work with.

#### Namespaces
It spawns a process with PID of 1, even though host PID is 5452, and makes it think it is alone.
````
sudo unshare --fork --pid --mount-proc bash
````
But it is still using host's all resources. We need to somehow limit it.

#### Cgroups
It controls how much CPU, memory and disk I/O container can use.
Without cgroups, one container could starve others of resources.

```
sudo mkdir /sys/fs/cgroup/julius -> create file in container
```

```
echo 10000000 | sudo tee /sys/fs/cgroup/julius/memory.max -> set memory limit
```

```
echo $$ | sudo tee /sys/fs/cgroup/julius/cgroup.procs -> add current shell into group
```

```
head -c 15M /dev/zero | tail -> test it, it should be Killed
```


Links:

202608312050

