We use `Deployment` to create `Linkding`. We also have to include `initContainers` to ensure that `postgres`, to which we want to connect, is ready. We can go without it but, in that case, our container will be in `CrashLoop` until db is up. So `initContainers` is clean and clear intent.

Example of `initContainers`:
```
initContainers: 
	- name: wait-for-db 
	  image: postgres:16-alpine 
	  command: 
		  - sh 
		  - -c 
		  - | 
		    until pg_isready -h postgres -p 5432; do 
			    echo "waiting for postgres..."; sleep 2 
			done
```



Links:

202609212255

