#### Deploy to cluster:
```bash
helm repo add argocd "https://argoproj.github.io/argo-helm" && helm repo update
```
```bash
helm upgrade --install argocd "argocd/argo-cd" -f values.yml -n argocd --version "6.7.10" --create-namespace
```
```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o go-template='{{.data.password | base64decode}}'
```

#### Get default values:
```bash
helm show values "argocd/argo-cd" > default-values.yml
```

#### Check updates:
```bash
helm search repo "argocd/argo-cd"
```

#### Get manifests:
```bash
helm template argocd "argocd/argo-cd" -f values.yml -n argocd --version "6.7.10" > manifests.yml
```

#### Enable monitoring:
```bash
kubectl apply -f monitoring.yml
```

#### URLs:
- [Docs](https://argo-cd.readthedocs.io/en/stable/)
- [Chart](https://github.com/argoproj/argo-helm/tree/main/charts/argo-cd)
- [Metrics](https://argo-cd.readthedocs.io/en/stable/operator-manual/metrics/)
- [Dashboard](https://github.com/argoproj/argo-cd/blob/master/examples/dashboard.json)
