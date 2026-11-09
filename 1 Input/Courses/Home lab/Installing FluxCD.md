- create new github repo
	- install `gh` and authenticate; use ssh key and authenticate via [https://github.com/login/device](https://github.com/login/device) by entering code that you get from CLI
- `gh repo create`
- setup personal access token, so that FluxCD can work with repo
	- Go to GitHub Settings > Developer Settings > Personal Access Tokens
	- Generate a new classic token with 'repo' permissions
	- Store the token in an environment variable: `export GITHUB_TOKEN=<your-token>`
	- Also export your GitHub username: `export GITHUB_USER=<your-username>`
- install `flux cli` - `curl -s https://fluxcd.io/install.sh | sudo bash`
- check cluster compatibility: `flux check --pre`
- bootstrap flux into our cluster:
```
flux bootstrap github \
--owner=$GITHUB_USER \
--repository=pi-cluster \
--branch=main \
--path=./clusters/staging \
--personal
```

This command connects flux controller to cluster and connects it to Github repo.
`branch` is branch that flux tracks, `personal` means cluster is personal, `path` cluster's config place, which means one repo can handle several clusters like `production`, `staging`.

When you run it, Flux does the following:
1. **Creates or clones the repo** on GitHub.
2. **Generates Flux’s own manifests** (source-controller, kustomize-controller, helm-controller, notification-controller) and commits them to `clusters/staging/flux-system/`.
3. **Installs those controllers** in the `flux-system` namespace on your current cluster, whichever one your kubeconfig points to.
4. **Creates an SSH deploy key**, adds the public half to the repo as a deploy key, and stores the private half as a Secret in the cluster. This is how Flux pulls from the repo afterward.
5. **Creates a `GitRepository` and a `Kustomization`** that tell Flux to watch `main` at `./clusters/staging` and apply whatever it finds there.

Links:

202611091829

