#### Install to cluster:
```bash
kubectl create namespace testing
```
```bash
helm show values "oci://ghcr.io/kube-logging/helm-charts/log-generator" > log-generator-default-values.yml
```
```bash
helm upgrade --install log-generator "oci://ghcr.io/kube-logging/helm-charts/log-generator" -f log-generator-values.yml -n testing
```

#### Enable log collecting:
```bash
kubectl apply -f test-output.yml
```
```bash
kubectl -n testing patch deployment log-generator -p '{"spec": {"template": {"metadata": {"annotations": {"promtail.io/collect": "true"}}}}}'
```

#### Get status:
```bash
kubectl -n testing port-forward svc/log-generator-api 11000
```
```bash
curl "http://localhost:11000/" | jq
```

#### URLs:
- [Docs](https://github.com/kube-logging/log-generator/blob/master/README.md)
- [Charts](https://github.com/kube-logging/log-generator/tree/master/charts/log-generator)
