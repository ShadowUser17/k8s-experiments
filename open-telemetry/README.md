### Warning! Required installed cert-manager.

#### Deploy to cluster:
```bash
helm repo add open-telemetry "https://open-telemetry.github.io/opentelemetry-helm-charts" && helm repo update
```
```bash
kubectl create namespace monitoring
```
```bash
helm upgrade --install otlp-operator "open-telemetry/opentelemetry-operator" -f values.yml -n monitoring --version "0.53.0"
```

#### Check updates:
```bash
helm search repo "open-telemetry/opentelemetry-operator"
```

#### Get default values:
```bash
helm show values "open-telemetry/opentelemetry-operator" > default-values.yml
```

#### Get manifests:
```bash
helm template otlp-operator "open-telemetry/opentelemetry-operator" -f values.yml -n monitoring --version "0.53.0" > manifests.yml
```

#### Get API resources:
```bash
kubectl api-resources | grep opentelemetry
```
```bash
kubectl get otelinsts -A
```
```bash
kubectl get otelcols -A
```

#### URLs:
- [what-is-opentelemetry](https://opentelemetry.io/docs/what-is-opentelemetry/)
- [opentelemetry-kubernetes](https://opentelemetry.io/docs/kubernetes/)
- [opentelemetry-vendors](https://opentelemetry.io/ecosystem/vendors/)
- [opentelemetry-operator-chart](https://github.com/open-telemetry/opentelemetry-helm-charts/tree/main/charts/opentelemetry-operator)
