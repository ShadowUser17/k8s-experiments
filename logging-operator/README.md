#### Install to cluster:
```bash
kubectl create namespace monitoring
```
```bash
helm upgrade --install logging-operator "oci://ghcr.io/kube-logging/helm-charts/logging-operator" -f values.yml -n monitoring --version "4.6.0"
```

#### Get default values:
```bash
helm show values "oci://ghcr.io/kube-logging/helm-charts/logging-operator" > default-values.yml
```

#### Export manifests:
```bash
helm template logging-operator "oci://ghcr.io/kube-logging/helm-charts/logging-operator" -f values.yml -n monitoring --version "4.6.0" > manifests.yml
```

#### Send logs to Loki:
```bash
kubectl apply -f loki-output.yml
```

#### Send logs to Elasticsearch:
```bash
kubectl apply -f es-output.yml
```

#### Get API resources:
```bash
kubectl api-resources | grep banzaicloud
```

#### Get logging configuration:
```bash
kubectl get logging logging-operator -o yaml
```
```bash
kubectl get fluentbitagents logging-operator -o yaml
```
```bash
kubectl -n monitoring get secret logging-operator-fluentd-app -o go-template='{{index .data "fluentd.conf" | base64decode}}'
```
```bash
kubectl -n monitoring get secret logging-operator-fluentbit -o go-template='{{index .data "fluent-bit.conf" | base64decode}}'
```

#### URLs:
- [Docs](https://kube-logging.dev/docs/)
- [Chart](https://github.com/kube-logging/logging-operator/tree/master/charts/logging-operator)
- [Dashboard](https://grafana.com/grafana/dashboards/7752-logging-dashboard/)
