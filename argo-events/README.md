#### Deploy to cluster:
```bash
kubectl create namespace argo-events
```
```bash
helm repo add argocd "https://argoproj.github.io/argo-helm" && helm repo update
```
```bash
helm upgrade --install argo-events "argocd/argo-events" -f values.yml -n argo-events --version "2.4.7"
```
```bash
kubectl apply -f eventbus.yml
```

#### Enable monitoring:
```bash
kubectl apply -f monitoring.yml
```

#### Get default values:
```bash
helm show values "argocd/argo-events" > default-values.yml
```

#### Check updates:
```bash
helm search repo "argocd/argo-events"
```

#### Get manifests:
```bash
helm template argo-events "argocd/argo-events" -f values.yml -n argo-events --version "2.4.7" > manifests.yml
```

#### URLs:
- [Docs](https://argoproj.github.io/argo-events/)
- [Chart](https://github.com/argoproj/argo-helm/tree/main/charts/argo-events)
- [Metrics](https://argoproj.github.io/argo-events/metrics/)
- [Examples](https://github.com/argoproj/argo-events/tree/master/examples)
