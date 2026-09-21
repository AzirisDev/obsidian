We can create one secret file and use it from different objects and put different names.
We can have one secret file:
```
...
stringData: username: linkding
...
```
Then in DB file, we can name it as following:
```
env: 
	- name: POSTGRES_USER 
	  valueFrom: { secretKeyRef: { name: linkding-db, key: username } }
```
But in `linkding` file, we can name it:
```
env:
	- name: LD_DB_USER 
	  valueFrom: { secretKeyRef: { name: linkding-db, key: username } }
```


Links:

202609212210

