#### Deploy to cluster:
```bash
helm repo add kedacore "https://kedacore.github.io/charts" && helm repo update
```
```bash
helm upgrade --install keda "kedacore/keda" -n keda --version "2.13.2" --create-namespace \
--set "prometheus.operator.enabled=true" \
--set "prometheus.webhooks.enabled=true" \
--set "prometheus.metricServer.enabled=true"
```

#### Check updates:
```bash
helm search repo "kedacore/keda"
```

#### Get default values:
```bash
helm show values "kedacore/keda" > default-values.yml
```

#### Get manifests:
```bash
helm template keda "kedacore/keda" -n keda --version "2.13.2" \
--set "prometheus.operator.enabled=true" \
--set "prometheus.webhooks.enabled=true" \
--set "prometheus.metricServer.enabled=true" > manifests.yml
```

#### URLs:
- [keda-concepts](https://keda.sh/docs/2.13/concepts/)
- [keda-deploy](https://keda.sh/docs/2.13/deploy/)
- [scaler-prometheus](https://keda.sh/docs/2.13/scalers/prometheus/)
