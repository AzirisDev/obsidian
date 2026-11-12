https://fluxcd.io/flux/guides/mozilla-sops/

We are going to use `SOPS` and `Age`. `SOPS` - toolkit for encrypting and decrypting Kubernetes secrets with OpenPGP, Age, AWS KMS, GCP KMS and Azure Key Vault. `Age` is simple key generation tool.

1) Install those tools: `brew install sops age`
2) Generate age-key pair: `age-keygen -o age.agekey`
3) Encrypting a secret
```
kubectl -n linkding create secret generic test-secret \
--from-literal=user=admin \
--from-literal=password=mischa \
--dry-run=client \
-o yaml > test-secret.yaml


export AGE_PUBLIC={public-key-from-age.key}


sops --age=$AGE_PUBLIC \
--encrypt --encrypted-regex '^(data|stringData)$' --in-place test-secret.yaml


cat test-secret.yaml
```
4) Add the private key to the cluster
```
# This adds age.key content into Kubernetes cluster.
# !!! BUT WE HAVE TO STORE THIS SECRET SOMEWHERE ELSE ALSO. Cause when cluster
# is got deleted or something, this secrets got deleted and we gotta setup
# this part again

cat age.agekey |
kubectl create secret generic sops-age \
--namespace=flux-system \
--from-file=age.agekey=/dev/stdin


# In the clusters/staging directory, add:

#.sops.yaml

creation_rules:
  - path_regex: .*.yaml
    encrypted_regex: ^(data|stringData)$
    age: {public-key-from-age.key}


# in the apps.yaml Kustomization file, add under spec:
# (same level as prune: true)

decryption:
    provider: sops
    secretRef:
      name: sops-age
```
5) Put our generated `test-secret.yaml` into `apps/staging/linkding`, add mention to the `kustomization.yaml` -> flux should deploy the secrets in `linkding` namespace



#### Make tunnel credentials and Lindking user & password encrypted

```
kubectl create secret generic tunnel-credentials \
--from-file=credentials.json=59c97568-9eda-4dbf-9857-b6cf9cf91259.json --dry-run=client -o yaml > cloudflare-secret.yaml

sops --age=$AGE_PUBLIC \
--encrypt --encrypted-regex '^(data|stringData)$' --in-place cloudflare-secret.yaml
```

```
kubectl create secret generic linkding-container-env \
--from-literal=LD_SUPERUSER_NAME=mykola \
--from-literal=LD_SUPERUSER_PASSWORD=avramuk \
--dry-run=client \
-o yaml > linkding-container-env-secret.yaml

```

```
envFrom:
  - configMapRef:
      name: linkding-configmap
  - secretRef:
      name: linkding-container-env
```


Links:

202611120704

