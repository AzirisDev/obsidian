Lets simulate falling container:
```
...
spec:
	containers:
		- image: httpd:alpine3.18
		  name: httpd
		  command: ["/bin/bash", "-c"] # override default command
		  args: ["sleep 5; exit 1"] # sleep and exit with error
...
```

 Status changes:
 `ContainerCreating` -> `RunContainerError` -> `CrashLoopBackOff` -> loop over only certain pods. It is not going over all pods. 

Links:

202609100905

