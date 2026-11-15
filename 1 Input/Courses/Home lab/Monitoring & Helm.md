We will deploy Helm charts using Flux using code and methodologies. We will be using `kube-prometheus-stack` as we did in [[Kube prometheus stack]] - but here we did it using CLI.

 Flux has custom resources called `HelmRepository` and `HelmRelease`.
 `HelmRepository` - adds the repository and make it updated, available in your machine.
 `HelmRelease` - install charts from that repository.

Repo structure:
```
├── apps
│   ├── base
│   └── staging
├── monitoring
│   ├── configs
│   └── controllers
└── clusters
    └── staging
```

We are going to put into `monitoring/controllers/base/kube-prometheus-stack` the `namespace.yaml`, `repository.yaml`, `release.yaml`, `kustomization.yaml`.

Also `kustomization.yaml` in `monitoring/controllers/staging/kube-prometheus-stack`.

`repository.yaml`
```
apiVersion: source.toolkit.fluxcd.io/v1
kind: HelmRepository
metadata:
  name: kube-prometheus-stack
  namespace: monitoring
spec:
  interval: 24h
  url: https://prometheus-community.github.io/helm-charts
```

`release.yaml`
```
apiVersion: helm.toolkit.fluxcd.io/v2
kind: HelmRelease
metadata:
  # Helm release name (shown in `helm list`)
  name: kube-prometheus-stack
  # Where this object lives + default install ns
  namespace: monitoring
spec:
  # Reconcile the release every 30 min:
  # check drift, apply values, upgrade if needed
  interval: 30m

  chart:
    # Template for a HelmChart object Flux creates
    spec:
      # Chart name inside the repository
      chart: kube-prometheus-stack
      # Exact pin. Ranges also work, e.g. "66.x",
      # then Flux auto-upgrades within the range
      version: "66.2.2"
      # Where to fetch the chart from
      sourceRef:
        kind: HelmRepository
        name: kube-prometheus-stack
        namespace: monitoring
      # How often to look for a new chart version
      # (only matters with a version range)
      interval: 12h

  install:
    # First install: create CRDs from chart
    # (default behaviour)
    crds: Create

  upgrade:
    # Upgrade: create new CRDs AND update old ones.
    # Plain Helm never updates CRDs; this chart's
    # operator CRDs change between versions
    crds: CreateReplace

  driftDetection:
    # Revert manual changes made in the cluster
    # (e.g. kubectl edit on a Deployment)
    mode: enabled
    ignore:
      # The operator's admission webhook adds this
      # annotation to every PrometheusRule. It is
      # not in the chart, so without this ignore
      # Flux would report drift forever
      - paths:
          - "/metadata/annotations/prometheus-operator-validated"
        target:
          kind: PrometheusRule

  # Same as values.yaml / --set in plain Helm
  values:
    grafana:
      # TODO: move to a Secret (SOPS), don't keep
      # passwords in Git in plain text
      adminPassword: azim
```

`CRDs - Custom Resource Definitions` - It registers the new kind with the API server, including its name, API group, version, and a schema describing which fields are allowed. After that, the API server stores and serves objects of that kind like any built-in one.

Port forward to see the monitoring dashboard
```
kubectl -n monitoring port-forward svc/kube-prometheus-stack-grafana 8080:80
```
This is annoying, so we will learn [[Ingress with Traefik]] to access monitoring stack via url.

Links:

202611130839

