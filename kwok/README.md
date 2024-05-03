#### Install CLI:
```bash
curl -L "https://github.com/kubernetes-sigs/kwok/releases/download/v${version}/kwok-linux-amd64" -o /usr/local/bin/kwok && \
chmod 755 /usr/local/bin/kwok
```
```bash
curl -L "https://github.com/kubernetes-sigs/kwok/releases/download/v${version}/kwokctl-linux-amd64" -o /usr/local/bin/kwokctl && \
chmod 755 /usr/local/bin/kwokctl
```

#### Show clusters:
```bash
kwokctl get clusters
```

#### Create cluster:
```bash
kwokctl create cluster --name testing
```

#### Create node:
```bash
kubectl apply -f node.yml
```

#### Delete cluster:
```bash
kwokctl delete cluster --name testing
```

#### URLs:
- [Docs](https://kwok.sigs.k8s.io/)
- [Releases](https://github.com/kubernetes-sigs/kwok/releases)
