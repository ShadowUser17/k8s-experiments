#### Install to cluster:
```bash
helm repo add cilium "https://helm.cilium.io" && helm repo update
```
```bash
helm upgrade --install tetragon "cilium/tetragon" -f values.yml -n kube-system --version "1.0.2"
```

#### Install CLI:
```bash
curl -LO "https://github.com/cilium/tetragon/releases/latest/download/tetra-linux-amd64.tar.gz" && \
tar -xzf tetra-linux-amd64.tar.gz tetra && mv ./tetra /usr/local/bin/ && rm -f tetra-linux-amd64.tar.gz
```

#### Check updates:
```bash
helm search repo "cilium/tetragon"
```

#### Get default values:
```bash
helm show values "cilium/tetragon" > default-values.yml
```

#### Export manifests:
```bash
helm template tetragon "cilium/tetragon" -f values.yml -n kube-system --version "1.0.2" > manifests.yml
```

#### Show logs:
```bash
kubectl logs -n kube-system -l "app.kubernetes.io/name=tetragon" -c export-stdout -f | tetra getevents -o compact
```

#### URLs:
- [docs](https://tetragon.cilium.io/docs/)
- [releases](https://github.com/cilium/tetragon/releases)
- [helm-chart](https://tetragon.cilium.io/docs/reference/helm-chart/)
- [capabilities](https://tetragon.cilium.io/docs/reference/grpc-api/)
