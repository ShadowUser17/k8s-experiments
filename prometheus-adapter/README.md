#### Deploy to cluster:
```bash
helm repo add prometheus-community "https://prometheus-community.github.io/helm-charts" && helm repo update
```
```bash
helm upgrade --install prom-adapter "prometheus-community/prometheus-adapter" -f values.yml -n monitoring --version "4.10.0"
```

#### Check updates:
```bash
helm search repo "prometheus-community/prometheus-adapter"
```

#### Get default values:
```bash
helm show values "prometheus-community/prometheus-adapter" > default-values.yml
```

#### Export manifests:
```bash
helm template prom-adapter "prometheus-community/prometheus-adapter" -f values.yml -n monitoring --version "4.10.0" > manifests.yml
```

#### Get available metrics:
```bash
kubectl get --raw "/apis/custom.metrics.k8s.io/v1beta1"
```
```bash
kubectl get --raw "/apis/custom.metrics.k8s.io/v1beta1/namespaces/*/metrics/<metric>"
```
```bash
kubectl get --raw "/apis/custom.metrics.k8s.io/v1beta1/namespaces/<ns>/pods/*/<metric>"
```
```bash
kubectl get --raw "/apis/custom.metrics.k8s.io/v1beta1/namespaces/<ns>/services/*/<metric>"
```

#### URLs:
- [Docs](https://github.com/kubernetes-sigs/prometheus-adapter/blob/master/README.md)
- [Chart](https://github.com/prometheus-community/helm-charts/tree/main/charts/prometheus-adapter)
- [Releases](https://github.com/kubernetes-sigs/prometheus-adapter/releases)
