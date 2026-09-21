Database needs stable domain name and own volume that follows it. For that, we can use `StatefulSet`: it will create stable pod names -  `<name>-<ordinal>` like `postgres-0` and auto-create [[Persistent storage]] sticked to it. 

We need to use `Headless Service` by two reasons:
- It is required to manage `StatefulSet`. Latter object has `serviceName` field and it provide stable network identity across the cluster.
- For databases, we need certain pod to read/write. Only per-pod DNS makes it possible to say "connect to `postgres-0".



Links:

202609212210

