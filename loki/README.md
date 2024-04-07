#### Add helm repo:
```bash
helm repo add grafana "https://grafana.github.io/helm-charts" && helm repo update
```
```bash
helm repo add bitnami "https://charts.bitnami.com/bitnami" && helm repo update
```

#### Get default values:
```bash
helm show values "grafana/loki" > loki-defaults.yml
```
```bash
helm show values "grafana/promtail" > promtail-defaults.yml
```
```bash
helm show values "bitnami/kubernetes-event-exporter" > event-exporter-defaults.yml
```

#### Install loki:
```bash
kubectl create namespace monitoring
```
```bash
helm upgrade --install loki "grafana/loki" -f loki.yml -n monitoring --version "5.47.2"
```

#### Install promtail:
```bash
helm upgrade --install promtail "grafana/promtail" -f promtail.yml -n monitoring --version "6.15.5"
```

#### Install kubernetes-event-exporter:
```bash
helm upgrade --install event-exporter "bitnami/kubernetes-event-exporter" -f event-exporter.yml -n monitoring --version "3.0.2"
```

#### Check updates:
```bash
helm search repo "grafana/loki"
```
```bash
helm search repo "grafana/promtail"
```
```bash
helm search repo "bitnami/kubernetes-event-exporter"
```

#### Export manifests:
```bash
helm template loki "grafana/loki" -f loki.yml -n monitoring --version "5.47.2" > loki-manifests.yml
```
```bash
helm template promtail "grafana/promtail" -f promtail.yml -n monitoring --version "6.15.5" > promtail-manifests.yml
```
```bash
helm template event-exporter "bitnami/kubernetes-event-exporter" -f event-exporter.yml -n monitoring --version "3.0.2" > event-exporter-manifests.yml
```

#### Enable log collection:
```yaml
template:
  metadata:
    annotations:
      promtail.io/collect: "true"
```

#### loki/promtail:
- [Docs](https://grafana.com/docs/loki/latest/)
- [Loki](https://github.com/grafana/loki/tree/main/production/helm/loki)
- [Promtail](https://github.com/grafana/helm-charts/tree/main/charts/promtail)
- [Releases](https://github.com/grafana/loki/releases)
- [Monitoring](https://grafana.com/docs/loki/latest/operations/observability/)

#### kubernetes-event-exporter:
- [Docs](https://github.com/resmoio/kubernetes-event-exporter)
- [Chart](https://github.com/bitnami/charts/tree/main/bitnami/kubernetes-event-exporter/)
- [Images](https://hub.docker.com/r/bitnami/kubernetes-event-exporter/tags)
