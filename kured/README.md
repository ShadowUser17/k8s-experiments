#### Install to cluster:
```bash
helm repo add kubereboot "https://kubereboot.github.io/charts" && helm repo update
```
```bash
helm upgrade --install krds "kubereboot/kured" -f values.yml -n kube-system --version "5.4.5"
```

#### Check updates:
```bash
helm search repo "kubereboot/kured"
```

#### Get default values:
```bash
helm show values "kubereboot/kured" > default-values.yml
```

#### Export manifests:
```bash
helm template krds "kubereboot/kured" -f values.yml -n kube-system --version "5.4.5" > manifests.yml
```

#### URLs:
- [Docs](https://kured.dev/docs/)
- [Chart](https://github.com/kubereboot/charts/tree/main/charts/kured)
