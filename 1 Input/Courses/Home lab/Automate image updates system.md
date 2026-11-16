 We have applications that points to certain container images, its versions. We are going to setup a system that checks the latest versions of them and update it.
 
 Here comes https://docs.renovatebot.com, `Renovate`. It check outs the repo every hour and creates pull request to update the image version with detailed description.

#### Steps to set up Renovate

1) Create kubernetes secret with github personal access token
2) Encrypt it with age key using sops
3) Create `infrastructure` directory, `staging/renovate` and `base/renovate` directories in it
4) Put here `namespace`, `renovate-container-env`, `cronjob`, `configmap` yaml files
5) CronJob file:
```
apiVersion: batch/v1
kind: CronJob
metadata:
  name: renovate
  namespace: renovate
spec:
  schedule: "@hourly"
  # Excludes possibilities of several cron jobs at a time
  concurrencyPolicy: Forbid
  jobTemplate:
    spec:
      template:
        spec:
          containers:
            - name: renovate
              image: renovate/renovate:latest
              args:
                - AzirisDev/tupac-cluster

              envFrom:
                - secretRef:
                  # Secret name
                    name: renovate-container-env
                - configMapRef:
                  # Config map pointer - environment fields
                    name: renovate-configmap

          restartPolicy: Never
```
6) ConfigMap file:
```
apiVersion: v1
kind: ConfigMap
metadata:
  name: renovate-configmap
  namespace: renovate
data:
  RENOVATE_AUTODISCOVER: "false"
  RENOVATE_GIT_AUTHOR: "Renovate Bot <bot@renovateapp.com>"
  RENOVATE_PLATFORM: "github"
```
7) Add all kustomization files in `infrastructure`, `clusters` directories. We also need to create new `infrastructure` yaml file in `clusters`.
8) Add json file to the root of cluster repo:
```
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "kubernetes": {
    "fileMatch": [
      "\\.yaml$"
    ]
  }
}
```


Links:

202611160809

