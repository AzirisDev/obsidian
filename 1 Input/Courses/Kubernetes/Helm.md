  It is package manager for k8s. It packages applications into `charts` so we can create, deploy, delete many apps with single commands instead of dealing with bunch of yaml files.
It does not run inside cluster, it is binary that runs on machine itself, separate software which talks to k8s via API.

Key stuff:
- `Chart` - a package with default values and metadata for k8s app
- `Values` - config for overriding template chart per environment - create values preserving default values yaml file hierarchy
- `Release` - deployed instance of chart in a cluster; it tracks `revision` history
- `Repository` - place where we store charts

Common commands:

- `helm repo add bitnami https://charts.bitnami.com/bitnami` - registers bitnami under that name locally, so you reference that further
- `helm install myapp bitnami/nginx` - deploys `nginx` chart from `bitnami` repo under name `myapp` - it is release now
- `helm upgrade myapp bitnami/nginx --set replicaCount=3` - upgrades replicas value in release to 3 and then bump the revision to 2
- `helm rollback myapp 1` - roll backs to revision 1 BUT it actually creates new revision, cause you can not override the journal itself
- `helm uninstall myapp` - Removes the release and all Kubernetes resources it created, and deletes its history.
- `helm show values <repo>/<chart> > values.yaml` - show and put the default values of chart to the file
-  

Links:

202609161537

