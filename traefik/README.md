#### Install to cluster:
```bash
helm repo add traefik "https://traefik.github.io/charts" && helm repo update
```
```bash
helm upgrade --install traefik "traefik/traefik" -n kube-system --version "27.0.0"
```

#### Check updates:
```bash
helm search repo "traefik/traefik"
```

#### Get default values:
```bash
helm show values "traefik/traefik" > default-values.yml
```

#### Get manifests:
```bash
helm template traefik "traefik/traefik" -n kube-system --version "27.0.0" > manifests.yml
```

#### URLs:
- [Docs](https://doc.traefik.io/traefik/)
- [Chart](https://github.com/traefik/traefik-helm-chart)
