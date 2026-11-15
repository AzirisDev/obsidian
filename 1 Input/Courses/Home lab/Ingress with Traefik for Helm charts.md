First, we have to add the repo of `helm-charts` to the machine.
```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
```

Then we have to get and put the helm values in `kube-prometheus-stack` to file:
`helm show values prometheus-community/kube-prometheus-stack > values.yaml`
We get here the ingress default values from here and put it into our `monitoring/controllers/base/release.yaml`.

We fill out the fields, put `hosts: - grafana.azimsattykov.org`, add this url to `cloudflare` and now it working. `Grafana` is now accessible via url, which points to our machine.

 BUT it is not secure!!!!!

#### Set up a TLS certificate
```
# Generate the private key and certificate
openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
  -keyout grafana.key \
  -out grafana.crt \
  -subj "/C=KZ/ST=Almaty/L=Almaty/O=Azim Home Lab/OU=Monitoring/CN=grafana.azimsattykov.org" \
  -addext "subjectAltName=DNS:grafana.azimsattykov.org"
```

Now we will create a kubernetes secret from those files:
```
kubectl create secret tls grafana-tls-secret \
  --cert=grafana.crt \
  --key=grafana.key \
  --namespace=monitoring \
  --dry-run=client \
  -o yaml > grafana-tls-secret.yaml
```

Now encrypt it with `sops`:
```
export AGE_PUBLIC=age1lepyq8krve8y8zuplpmcgtar66a5zglr82k90cr3t0aa3yg7lesstsnfk4

sops --age=$AGE_PUBLIC \
--encrypt --encrypted-regex '^(data|stringData)$' --in-place grafana-tls-secret.yaml
```

Now move these secret file to `monitoring/configs/staging/kube-prometheus-stack`. Add kustomization files.

In `clusters/staging/monitoring.yaml` kustomization file add the config for `monitoring/configs` directory and add here:
```
decryption:
  provider: sops
  secretRef:
    name: sops-age
```

Do not forget to twick the `tls` field in `monitoring/controllers/base/kube-prometheus-stack/release.yaml`.

Links:

202611132128

