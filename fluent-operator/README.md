#### Install to cluster:
```bash
helm repo add fluent "https://fluent.github.io/helm-charts" && helm repo update
```
```bash
kubectl create namespace monitoring
```
```bash
helm upgrade --install fluent-operator "fluent/fluent-operator" -f fluent-operator-values.yml -n monitoring --version "2.7.0"
```

#### Enable monitoring:
```bash
kubectl apply -f fluent-bit-monitoring.yml
```

#### Check updates:
```bash
helm search repo "fluent/fluent-operator"
```

#### Get default values:
```bash
helm show values "fluent/fluent-operator" > fluent-operator-default-values.yml
```

#### Get manifests:
```bash
helm template fluent-operator "fluent/fluent-operator" -f fluent-operator-values.yml -n monitoring --version "2.7.0" > manifests.yml
```

#### Get API resources:
```bash
kubectl api-resources | grep fluent
```

#### Get configuration:
```bash
kubectl get cfbc -o yaml
```
```bash
kubectl get cfdc -o yaml
```

#### URLs:
- [fluent-operator](https://github.com/fluent/fluent-operator/blob/master/README.md)
- [fluent-bit-docs](https://docs.fluentbit.io/manual)
- [fluent-chart](https://github.com/fluent/helm-charts/tree/main/charts/fluent-operator)
- [monitoring](https://docs.fluentbit.io/manual/administration/monitoring)
- [dashboard](https://grafana.com/grafana/dashboards/7752-logging-dashboard/)
