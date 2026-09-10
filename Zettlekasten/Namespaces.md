It is used to isolate virtually the resources of one cluster. You can have several clusters in one cluster. It can be used to deploy many environments (`dev, stage, prod`), isolate different teams' work.

- `kubectl get namespaces`
- `kubectl create namespace tamak` - create new namespace
- `kubectl create namespace tamak -o yaml --dry-run=client > tamak-ns.yaml` - create namespace yaml file
- `kubectl delete namespace tamak`


But depending on k8s configuration, current-context might point to `default` namespace. So if you do not specifically point to namespace during pods/deployments creation:
	`kubectl run test-pod --image=nginx --namespace=tamak` 
It will run in `default` namespace.

 Same for getting pods and all commands:
	 `kubectl get pods -n tamak`

#### How do we switch pointing namespace? Default one?

- `kubectl config current-context` - shows current context cluster
- `kubectl config set-context --current --namespace=tamak` - we get current context and change it's default pointing namespace to ours
 
 

Links:

202609101127

