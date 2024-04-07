#### Before installation:
- Add `--disable traefik` to installation script.
- Required installed cert-manager.

#### Install ingress to cluster:
```bash
helm repo add ingress-nginx "https://kubernetes.github.io/ingress-nginx" && helm repo update
```
```bash
helm upgrade --install ingress-nginx "ingress-nginx/ingress-nginx" -f values.yml -n ingress-nginx --version "4.10.0" --create-namespace
```

#### Check updates:
```bash
helm search repo "ingress-nginx/ingress-nginx"
```

#### Get default values:
```bash
helm show values "ingress-nginx/ingress-nginx" > default-values.yml
```

#### Get manifests:
```bash
helm template ingress-nginx "ingress-nginx/ingress-nginx" -f values.yml -n ingress-nginx --version "4.10.0" > manifests.yml
```

#### Enable monitoring:
```bash
kubectl apply -f monitoring.yml
```

#### URLs:
- [k3s-networking-docs](https://docs.k3s.io/networking)
- [k8s-ingress-concepts](https://kubernetes.io/docs/concepts/services-networking/ingress/)
- [k8s-ingress-nginx-docs](https://kubernetes.github.io/ingress-nginx/)
- [k8s-ingress-nginx-chart](https://github.com/kubernetes/ingress-nginx/tree/main/charts/ingress-nginx)
- [k8s-ingress-nginx-releases](https://github.com/kubernetes/ingress-nginx/releases)
- [k8s-ingress-nginx-dashboards](https://github.com/kubernetes/ingress-nginx/tree/main/deploy/grafana/dashboards)
