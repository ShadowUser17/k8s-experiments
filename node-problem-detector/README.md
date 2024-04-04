#### Install to cluster:
```bash
kubectl create namespace monitoring
```
```bash
helm repo add deliveryhero "https://charts.deliveryhero.io/" && helm repo update
```
```bash
helm upgrade --install node-monitor "deliveryhero/node-problem-detector" -f values.yml -n monitoring --version "2.3.12"
```

#### Check updates:
```bash
helm search repo "deliveryhero/node-problem-detector"
```

#### Get default values:
```bash
helm show values "deliveryhero/node-problem-detector" > default-values.yml
```

#### Export manifests:
```bash
helm template node-monitor "deliveryhero/node-problem-detector" -f values.yml -n monitoring --version "2.3.12" > manifests.yml
```

#### Get available pods:
```bash
kubectl -n monitoring get pods -o wide -l "app.kubernetes.io/name=node-problem-detector"
```

#### URLs:
- [Docs](https://github.com/kubernetes/node-problem-detector/blob/master/README.md)
- [Chart](https://github.com/deliveryhero/helm-charts/tree/master/stable/node-problem-detector)
