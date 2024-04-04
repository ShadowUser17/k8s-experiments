#### Install to cluster:
```bash
helm repo add aqua "https://aquasecurity.github.io/helm-charts" && helm repo update
```
```bash
helm upgrade --install tracee "aqua/tracee" -f values.yml -n tracee-system --version "0.20.0" --create-namespace
```

#### Check updates:
```bash
helm search repo "aqua/tracee"
```

#### Get default values:
```bash
helm show values "aqua/tracee" > default-values.yml
```

#### Export manifests:
```bash
helm template tracee "aqua/tracee" -f values.yml -n tracee-system --version "0.20.0" > manifests.yml
```

#### Show logs:
```bash
kubectl logs -f "daemonset/tracee" -n tracee-system
```

#### Get policies:
```bash
kubectl get policies -A
```

#### URLs:
- [Docs](https://aquasecurity.github.io/tracee/latest/docs/overview/)
- [Releases](https://github.com/aquasecurity/tracee/releases)
- [Dashboard](https://aquasecurity.github.io/tracee/latest/tutorials/deploy-grafana-dashboard/)
