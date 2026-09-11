Networking in k8s happens on pods level. Each Pod has its own IP address within cluster.
Pods can communicate with each other. Containers within one pod can communicate via localhost.

We can limit network communication via `Network Policies`.

How k8s does this networking? How do we put `Network Card` into our mini computers?
It manages it via [[Container Networking Interface Plugin]].


Pods are ephemeral, they die, the recreated, failed, etc. So how do we navigate traffic to certain pod or set of pods if they have unstable life-span?

[[Services]] comes for help.

Now we exposed `http://localhost:9000` via `LoadBalancer` Service to reach out our running deployment. Now imagine we need many things to reach and also it is hard during scaling. 
Here we have [[Ingress]] for help.

Links:

202609111152

