GitOps is set of best practices to control cluster in declarative way from manifests sitting in Git. It includes infrastructure and applications as code. It uses automation for updates and rollbacks.

Cluster might have Flux/Argo CD controller that will listen and pull any changes from Git by `reconciliation loop` - constant match of git state and cluster state.

For homelab, `Flux CD` is chosen over `Argo CD` because:
- Simpler setup and interface
- Encourages CLI usage
- Heavy reliance on `Kustomization` for manifest management

#### Kustomize 

Templating language for Kubernetes manifests. In simple terms, you have lego house - it is your `base`. Now you want to build another 3 with different attributes like red door, blue window. Via kustomize, you can just add notes to it and then built them. The best part, when you want to change roof of your `base` house, you do not have to rebuild in all places.
**That’s Kustomize!**
- The **LEGO house** is your Kubernetes YAML files (the base).
- The **sticky notes** are overlays (dev, prod, etc.).
- **Kustomize** is the helper who reads the sticky note and builds the right version for you.

```
app/
├── base/
│   ├── deployment.yaml
│   ├── service.yaml
│   └── kustomization.yaml
└── overlays/
    ├── dev/
    │   └── kustomization.yaml
    └── prod/
        ├── kustomization.yaml
        └── replicas-patch.yaml
```

Links:

202611091534

