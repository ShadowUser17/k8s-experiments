#### Install to cluster:
```bash
helm repo add aqua "https://aquasecurity.github.io/helm-charts" && helm repo update
```
```bash
helm upgrade --install trivy-operator "aqua/trivy-operator" -f values.yml -n trivy-system --version "0.21.4" --create-namespace
```

#### Check updates:
```bash
helm search repo "aqua/trivy-operator"
```

#### Get default values:
```bash
helm show values "aqua/trivy-operator" > default-values.yml
```

#### Get manifests:
```bash
helm template trivy-operator "aqua/trivy-operator" -f values.yml -n trivy-system --version "0.21.4" > manifests.yml
```

#### Show reports:
```bash
kubectl get clustervuln -o wide
```
```bash
kubectl get vulns -o wide -A
```
```bash
kubectl get clusterconfigaudit -o wide
```
```bash
kubectl get configaudits -o wide -A
```

#### URLs:
- [Docs](https://aquasecurity.github.io/trivy-operator/latest/docs/vulnerability-scanning/)
- [Metrics](https://aquasecurity.github.io/trivy-operator/latest/tutorials/integrations/metrics/)
- [Releases](https://github.com/aquasecurity/trivy-operator/releases)
- [Dashboard](https://grafana.com/grafana/dashboards/17813-trivy-operator-dashboard/)
