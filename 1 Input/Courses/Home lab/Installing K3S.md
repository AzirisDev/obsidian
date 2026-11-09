We can install k3s using this quick guide https://docs.k3s.io/quick-start. 
We also going to disable `Helm controller`. It is cluster resources controller similar to [[Deployments]] - it installs add-ons, chart releases.

We are going to use [[GitOps]] with Flux, it has its own custom resource controller. 

#### Commands
```
sudo su - # installation needs root user

curl -sfL https://get.k3s.io | INSTALL_K3S_EXEC="--disable=helm-controller" sh

kubectl get pods # should give response
```

Now we can talk to cluster on server, but not on working machine or anywhere. For that purpose, we need to copy `kube config` file to our working machine. You don’t log into the control plane; you keep a kubeconfig locally and talk to the API remotely.


#### Copy kube config file

File is located in `/etc/rancher/k3s/k3s.yaml`. At first only root user has permissions and ownership over that file, we will change it to be able to copy.

- `chown tupac:tupac /etc/rancher/k3s/k3s.yaml`
- exit the server
- `scp tupac:/etc/rancher/k3s/k3s.yaml .`

If you take a look inside the config, you will see that server field is pointing to localhost like `127.0.0.1`. It worked for server itself, but for us, we need to change it to real IP Address of the server, for example, 192.168.1.154.
- `mkdir ~/.kube`
- `mv k3s.yaml .kube/config`




Links:

202611091152

