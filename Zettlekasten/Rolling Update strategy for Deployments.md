Strategy is how we will replaces old pods with new ones.
It can be:
- `Recreate` -> kill all pods before creating new ones
- `RollingUpdate` -> rollout pods graudally
	- `maxUnavailable` - numbers of pods we can kill from replicas
	- `maxSurge` - how many more pods (dying, creating, alive) we can have
```yaml
strategy:
   type: RollingUpdate
   rollingUpdate:
     maxUnavailable: 1
     maxSurge: 1
```
We can also set it as percentage like `maxUnavailabe: 25%`.

```Hint
watch -n 1 "kubectl get pods" -> it will run every seconds this command
```

 
Links:

202609100851

