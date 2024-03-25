#### Deploy to cluster:
```bash
kubectl create namespace keptn-system
```
```bash
kubectl apply -f keptn-certs.yml
```
```bash
helm repo add keptn "https://charts.lifecycle.keptn.sh" && helm repo update
```
```bash
helm upgrade --install keptn "keptn/keptn" -f keptn-values.yml -n keptn-system --version "0.5.2" --wait
```

#### Enable monitoring:
```bash
kubectl apply -f keptn-monitor.yml
```

#### Check updates:
```bash
helm search repo "keptn/keptn"
```

#### Get default values:
```bash
helm show values "keptn/keptn" > keptn-defaults.yml
```

#### Get API resources:
```bash
kubectl api-resources | grep keptn.sh
```

#### URLs:
- [Docs](https://keptn.sh/stable/docs/)
- [Chart](https://github.com/keptn/lifecycle-toolkit/tree/main/chart)
- [Releases](https://github.com/keptn/lifecycle-toolkit/releases)
