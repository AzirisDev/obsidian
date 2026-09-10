It manages set of identical Pods, matching the desired state to real one. Hierarchy of controlling is this: `Depolyments` -> `ReplicaSet` -> `Pods`. We put desired state, including replicas count, rollout strategy, rollbacks, scaling, self-healing, into `yaml` and Deployments manages them.

- `kubectl create deploy` - main command to create deployment.
- `kubectl create deploy my-nginx --image-nginx --replicas=3` - create nginx Deployment with 3 replicas running
- `kubectl get deployments.apps` - get running deployments
- `kubectl edit deployments.apps my-nginx` - edit yaml file of selected deployment
- `kubectl describe deployments.apps my-nginx` - readable yaml file
- `kubectl delete deployments.apss my-nginx` - delete deployment

[[YAML file for deployment]]
[[How Deployments handle failing update of new pods?]]
[[Namespaces]]

 

Links:

202609091627

