We can set in deployment `Security context` adding following informations:
- `runAsUser`
- `runAsGroup`
- `fsGroup` - file-system group, shows which group owns the mounted volumes

We also restrict the privilege to escalate to the root.

in `deployment.yaml`:
```
...
    spec:
      securityContext:
        fsGroup: 33 # www-data group ID
        runAsUser: 33 # www-data user ID
        runAsGroup: 33 # www-data group ID

      containers:
		  ...

          securityContext:
            allowPrivilegeEscalation: false
...
```

Links:

202611111031

