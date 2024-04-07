#### Deploy to cluster:
```bash
helm repo add prometheus-community "https://prometheus-community.github.io/helm-charts" && helm repo update
```
```bash
helm upgrade --install prober "prometheus-community/prometheus-blackbox-exporter" -f values.yml -n monitoring --version "8.13.0"
```

#### Check updates:
```bash
helm search repo "prometheus-community/prometheus-blackbox-exporter"
```

#### Get default values:
```bash
helm show values "prometheus-community/prometheus-blackbox-exporter" > default-values.yml
```

#### Get manifests:
```bash
helm template prober "prometheus-community/prometheus-blackbox-exporter" -f values.yml -n monitoring --version "8.13.0" > manifests.yml
```

#### URLs:
- [Docs](https://github.com/prometheus/blackbox_exporter/blob/master/README.md)
- [Chart](https://github.com/prometheus-community/helm-charts/tree/main/charts/prometheus-blackbox-exporter)
- [Releases](https://github.com/prometheus/blackbox_exporter/releases)
