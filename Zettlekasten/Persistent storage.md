`PVC - PersistentVolumeClaims` - storage piece that was configured by administrated or provisioned with k8s after you claim some piece of storage. It lives as yaml object.

Example:
```
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: mealie-data
  namespace: tamak
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 500Mi
```

change in deployment pod the volumes part:
```
...
containers:
  - image: ghcr.io/mealie-recipes/mealie:v3.25.1
    name: mealie
    ports:
      - containerPort: 9000
    volumeMounts:
      - mountPath: /app/data
        name: mealie-data
volumes:
  - name: mealie-data
    persistentVolumeClaim:
      claimName: mealie-data
...
```

  
`kubectl get pvc` - get persistent volumes 

We have also `Storage Classes` - it is way how k8s will provision the storage. 
`kubectl get storageclasses.storage.k8s.io`
It is like a recipe to create a volume. It says _"when someone claims storage of this type, here's how to create the disk automatically."_

We have `Acess Modes` - how this storage can be accessed: `ReadWriteOnce`, `ReadWriteOnce`, `ReadWriteOncePod`, `ReadOnlyMany`, `ReadWriteMany`, `ReadWriteOncePod`.

Links:

202609152003

