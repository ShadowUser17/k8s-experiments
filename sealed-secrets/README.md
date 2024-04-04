#### Install to cluster:
```bash
helm repo add sealed-secrets "https://bitnami-labs.github.io/sealed-secrets" && helm repo update
```
```bash
helm upgrade --install sealed-secrets "sealed-secrets/sealed-secrets" -n kube-system --version "2.15.3"
```

#### Check updates:
```bash
helm search repo "sealed-secrets/sealed-secrets"
```

#### Get default values:
```bash
helm show values "sealed-secrets/sealed-secrets" > default-values.yml
```

#### Get manifests:
```bash
helm template sealed-secrets "sealed-secrets/sealed-secrets" -n kube-system --version "2.15.3" > manifests.yml
```

#### Install CLI:
```bash
curl -L "https://github.com/bitnami-labs/sealed-secrets/releases/download/v${version}/kubeseal-${version}-linux-amd64.tar.gz" -o "kubeseal-linux-amd64.tar.gz" && \
tar -xzf kubeseal-linux-amd64.tar.gz kubeseal && mv ./kubeseal /usr/local/bin/ && rm -f kubeseal-linux-amd64.tar.gz
```

#### URLs:
- [Docs](https://github.com/bitnami-labs/sealed-secrets/blob/main/README.md)
- [Chart](https://github.com/bitnami-labs/sealed-secrets/tree/main/helm/sealed-secrets)
- [Releases](https://github.com/bitnami-labs/sealed-secrets/releases)
