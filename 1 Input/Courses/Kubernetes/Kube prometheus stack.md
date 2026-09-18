 https://github.com/prometheus-community/helm-charts/tree/main/charts/kube-prometheus-stack
 
 It is monitoring stack of k8s cluster. Download using [[Helm]].
 ![[Screenshot 2026-09-18 at 12.16.38.png]]

- `Alert manager` - manages thresholds surpassing and notifies the admins
- `Kube prom prometheus` - gets and stores the metrics with timestamps
- `Grafana` - visualizes the metrics in graphs, charts, etc
- `Prom operator` - simplifies deployment and configuration of grafana and prometheus
- `State metrics` - listens to kube API server and collects info about state and metrics of kube objects
- `Node exporter` -  get metrics that node exposes

What can we do to see `Grafana` dashboards?
1) `Port-forward` the grafana service via `k9s` 
2) `LoadBalancer` service that replicates the `selector` of already provided prometheus stack



Links:

202609181215

