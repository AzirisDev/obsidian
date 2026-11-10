homelab cluster link: https://github.com/AzirisDev/tupac-cluster

We have this guide of ways of structuring the repo: https://fluxcd.io/flux/guides/repository-structure/

We are going to implement this structure:
```
├── apps
│   ├── base
│   ├── production 
│   └── staging
├── infrastructure
│   ├── base
│   ├── production 
│   └── staging
└── clusters
    ├── production
    └── staging
```
It is good for home-lab. There ways to do it as repo per team, environment, app as well.

#### Structure of home lab

Initial setup of linkding:
```
├── apps
│   ├── base
|   |   └── linkding
|	|       ├── deployment.yaml
|	|       ├── namespace.yaml
|	│       └── kustomization.yaml
│   └── staging
|       └── linkding
	│       └── kustomization.yaml
└── clusters
    └── staging
        ├── flux-system
	    |   ├── gotk-components.yaml
	    |   ├── gotk-sync.yaml
	    |   └── kustomization.yaml
        └── apps.yaml
```

Files under `flux-system` are generated during `flux bootstrap` and currently flux is set up above our k3s cluster. 
	`gotk-components.yaml` contains flux itself: resources and controllers
	`gotk-sync.yaml` contains `GitRepository` - which repo to watch; `Kustomization` - tells apply everything under this path like `./clusters/staging`. It also includes `apps.yaml`

`apps.yaml` is also `Kustomization` that tells reconcile `./apps/staging` path. It refers to `GitRepository` resource that we created in `gotk-sync.yaml`.
`apps/staging/linkding/kustomization.yaml` is `Kustomization` that tells to take a look at base layer of linkding -> `resources: - ../../base/linkding`
`apps/base/linkding/kustomization.yaml` again `Kustomization` lists what is make up the base.


After all setup, you can do port-forwarding and check result in browser:
`kubectl port-forward pod/linkding 8080:9090`



Links:

202611101818

