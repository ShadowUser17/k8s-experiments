#### Deploy to cluster:
```bash
kubectl create namespace argo-workflows
```
```bash
kubectl create namespace argo-workflows-workers
```
```bash
kubectl apply -f minio-secret.yml
```
```bash
helm repo add argocd "https://argoproj.github.io/argo-helm" && helm repo update
```
```bash
helm upgrade --install argo-workflows "argocd/argo-workflows" -f values.yml -n argo-workflows --version "0.41.11"
```

#### Get access:
```bash
kubectl apply -f argo-workflows-ui.yml
```
```bash
kubectl -n argo-workflows get secret argo-workflows-ui.service-account-token -o go-template='{{"Bearer "}}{{.data.token|base64decode}}{{"\n"}}'
```

#### Enable monitoring:
```bash
kubectl apply -f monitoring.yml
```

#### Auto delete for created resources:
```yaml
metadata:
  ownerReferences:
    - apiVersion: "argoproj.io/v1alpha1"
      kind: "Workflow"
      name: "{{ workflow.name }}"
      uid: "{{ workflow.uid }}"
```

#### Get default values:
```bash
helm show values "argocd/argo-workflows" > default-values.yml
```

#### Check updates:
```bash
helm search repo "argocd/argo-workflows"
```

#### Get manifests:
```bash
helm template argo-workflows "argocd/argo-workflows" -f values.yml -n argo-workflows --version "0.41.11" > manifests.yml
```

#### URLs:
- [Docs](https://argo-workflows.readthedocs.io/en/latest/)
- [Chart](https://github.com/argoproj/argo-helm/tree/main/charts/argo-workflows)
- [Metrics](https://argo-workflows.readthedocs.io/en/latest/metrics/)
- [Examples](https://github.com/argoproj/argo-workflows/tree/main/examples)
