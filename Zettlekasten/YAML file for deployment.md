To get generated yaml file, it is the same as [[Declarative method to run pod -> yaml files]] using `dry-run` flag.

`kubectl create deploy my-nginx --image-nginx --replicas=10 --dry-run=client -o yaml > deploy.yaml`

 Now run `kubectl apply -f deploy` create deployment. But now we have desired state in code. We can put it into git and have one source of truth.

[[Rolling Update strategy for Deployments]]


Links:

202609100845

