## Symptom

After creating an AKS cluster and fetching credentials:

```bash
az aks get-credentials --resource-group aks-manual --name aks-manual --overwrite-existing
# Merged "aks-manual" as current context in /home/tupac/.kube/config
```

`kubectl get pods -A` still showed the **old k3s cluster pods**, not AKS.

Then `kubectl config use-context aks-manual` failed with:

```
error: open /etc/rancher/k3s/k3s.yaml.lock: permission denied
```

## Root cause

> [!info] Two things were going on
> 
> 1. **kubectl was reading the k3s config, not `~/.kube/config`.**
>     - `az aks get-credentials` always writes to `~/.kube/config`.
>     - On a machine with k3s, `/usr/local/bin/kubectl` is a **symlink to the `k3s` binary**. When `KUBECONFIG` is unset, it defaults to `/etc/rancher/k3s/k3s.yaml`.
>     - Or `KUBECONFIG` was pointing at `/etc/rancher/k3s/k3s.yaml` in the shell config.
> 2. **`/etc/rancher/k3s/k3s.yaml` is owned by root.**
>     - `kubectl config use-context` writes to the kubeconfig files and creates a `.lock` file next to them.
>     - A normal user can't create the lock file in `/etc/rancher/k3s/`, which causes `permission denied`.

## Diagnosis commands

```bash
which kubectl                    # /usr/local/bin/kubectl
ls -l /usr/local/bin/kubectl     # -> k3s  (k3s's built-in kubectl)
echo $KUBECONFIG                 # which file(s) kubectl reads
kubectl config current-context
kubectl config get-contexts
```

## Fix (step by step)

```bash
# 1. Find where KUBECONFIG is set
grep -n KUBECONFIG ~/.bashrc ~/.profile ~/.zshrc 2>/dev/null

# 2. Remove old KUBECONFIG lines (backup saved as ~/.bashrc.bak)
sed -i.bak '/KUBECONFIG/d' ~/.bashrc

# 3. Copy k3s config into home and take ownership
mkdir -p ~/.kube
sudo cp /etc/rancher/k3s/k3s.yaml ~/.kube/k3s.yaml
sudo chown $USER:$USER ~/.kube/k3s.yaml
chmod 600 ~/.kube/config ~/.kube/k3s.yaml

# 4. Merge both configs via KUBECONFIG (files you own)
echo 'export KUBECONFIG=$HOME/.kube/config:$HOME/.kube/k3s.yaml' >> ~/.bashrc

# 5. Reload
source ~/.bashrc
echo $KUBECONFIG

# 6. Check contexts
kubectl config get-contexts

# 7. Rename the k3s context (default name is "default")
kubectl config rename-context default k3s-dell

# 8. Switch to AKS and verify
kubectl config use-context aks-manual
kubectl get nodes        # aks-nodepool1-xxxxx-vmss000000
kubectl get pods -A
```

## Switching between clusters

```bash
kubectl config get-contexts
kubectl config use-context aks-manual
kubectl config use-context k3s-dell

# One-off command against a specific cluster without switching
kubectl --context aks-manual get pods -A
```

> [!tip] Quality of life
> 
> - `kubectx` / `kubens` make switching contexts and namespaces quick.
> - Show the current context in your shell prompt (e.g. the starship `kubernetes` module) so you never run commands against the wrong cluster.

## Gotchas

> [!warning]
> 
> - **Never point `KUBECONFIG` at `/etc/rancher/k3s/k3s.yaml` directly.** It's root-owned, so context switches fail with lock-file errors.
> - **Don't mix `sudo` and non-sudo** for `az` and `kubectl`. Root has its own `~/.kube/config`.
> - **If k3s rotates its certificates**, copy `k3s.yaml` into `~/.kube/` again.
> - The k3s kubeconfig points to `https://127.0.0.1:6443`. To use it from another machine, change `server:` to the node's IP.

## Key takeaways

- `az aks get-credentials` → writes to `~/.kube/config` (or the file given with `--file`).
- k3s's bundled `kubectl` → defaults to `/etc/rancher/k3s/k3s.yaml` when `KUBECONFIG` is unset.
- `KUBECONFIG` can list multiple files separated by `:`. kubectl merges them into one view.
- Every kubeconfig file in `KUBECONFIG` must be writable by your user for `use-context` and `rename-context` to work.

## Related

- [[AKS - Azure Kubernetes Service]]
- [[Installing K3S]]

Links:

202611201718

