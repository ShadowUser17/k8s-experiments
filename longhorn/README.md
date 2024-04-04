#### Before installation:
- Add `--disable local-storage` to installation script.
- Install `open-iscsi` on the worker nodes.

#### Install to cluster:
```bash
helm repo add longhorn "https://charts.longhorn.io" && helm repo update
```
```bash
helm upgrade --install longhorn "longhorn/longhorn" -f values.yml -n longhorn-system --create-namespace --version "1.4.4"
```

#### Create ingress:
```bash
kubectl apply -f "https://raw.githubusercontent.com/ShadowUser17/BasicInstalls/master/kubernetes-operators/longhorn/frontend-ingress.yml"
```

#### Enable monitoring:
```bash
kubectl apply -f "https://raw.githubusercontent.com/ShadowUser17/BasicInstalls/master/kubernetes-operators/longhorn/prom-operator.yml"
```

#### Get API resources:
```bash
kubectl api-resources | grep longhorn
```

#### Check updates:
```bash
helm search repo "longhorn/longhorn"
```

#### Get default values:
```bash
helm show values "longhorn/longhorn" --version "1.4.4" > default-values.yml
```

#### Get manifests:
```bash
helm template longhorn "longhorn/longhorn" -f values.yml -n longhorn-system --version "1.4.4" > manifests.yml
```

#### URLs:
- [Docs](https://longhorn.io/docs/1.4.4/)
- [Chart](https://github.com/longhorn/charts/tree/v1.4.x/charts/longhorn)
- [Releases](https://github.com/longhorn/longhorn/releases)
- [Dashboard](https://grafana.com/grafana/dashboards/17626-longhorn-example-v1-4-0/)
