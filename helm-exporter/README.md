#### Deploy to cluster:
```bash
helm repo add sstarcher "https://shanestarcher.com/helm-charts/" && helm repo update
```
```bash
helm upgrade --install helm-exporter "sstarcher/helm-exporter" -f values.yml -n testing
```

#### Check updates:
```bash
helm search repo "sstarcher/helm-exporter"
```

#### Get default values:
```bash
helm show values "sstarcher/helm-exporter" > default-values.yml
```

#### URLs:
- [Docs](https://github.com/sstarcher/helm-exporter/blob/master/README.md)
- [Chart](https://github.com/sstarcher/helm-exporter/tree/master/helm)
