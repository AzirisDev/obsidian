`emptyDir` — created empty when the pod starts, deleted when the pod is removed. Used for scratch space or sharing files between containers.
```
apiVersion: 1
kind: Pod
metadata:
	labels:
	name: nginx-storage
spec:
	containers:
		- image: nginx
		  name: nginx
		  volumeMounts:
			  - mountPath: /scratch
			    name: scratch-volume
		- image: busybox
		  name: busybox
		  command: ["/bin/sh", "-c"]
		  args: ["sleep 1000" ]
		  volumeMounts:
			  - mountPath: /scratch
			    name: scratch-volume
	volumes:
		- name: scratch-volume
		  emptyDir:
			  sizeLimit: 500Mi
```

`kubectl exec -it nginx-storage -c <container-name> -- bash` - enter certain container in pod. 

Links:

202609152003

