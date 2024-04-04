#### Install to cluster:
```bash
helm repo add cilium "https://helm.cilium.io/" && helm repo update
```
```bash
helm upgrade --install cilium "cilium/cilium" -f values.yml -n kube-system --version "1.15.3"
```

#### Check updates:
```bash
helm search repo "cilium/cilium"
```

#### Get default values:
```bash
helm show values "cilium/cilium" > default-values.yml
```

#### Export manifests:
```bash
helm template cilium "cilium/cilium" -f values.yml -n kube-system --version "1.15.3" > manifests.yml
```

#### Get API resources:
```bash
kubectl api-resources | grep cilium
```

#### Install Cilium CLI:
```bash
curl -L "https://github.com/cilium/cilium-cli/releases/download/v${version}/cilium-linux-amd64.tar.gz" -o cilium-linux.tgz && \
tar -xzf cilium-linux.tgz cilium && mv ./cilium /usr/local/bin/ && rm -f ./cilium-linux.tgz
```

#### Install Hubble CLI:
```bash
curl -L "https://github.com/cilium/hubble/releases/download/v${version}/hubble-linux-amd64.tar.gz" -o hubble-linux.tgz && \
tar -xzf hubble-linux.tgz hubble && mv ./hubble /usr/local/bin/ && rm -f ./hubble-linux.tgz
```

#### Validate Cilium:
```bash
cilium status --wait
```

#### Validate network connectivity:
```bash
cilium connectivity test
```

#### Validate Hubble:
```bash
cilium hubble port-forward &
```
```bash
hubble status
```

#### Docs:
- [what-is-ebpf](https://ebpf.io/what-is-ebpf)
- [cilium-docs](https://docs.cilium.io/en/stable/)
- [hubble-docs](https://github.com/cilium/hubble/blob/master/Documentation/README.md)
- [observability](https://docs.cilium.io/en/stable/observability/metrics/)

#### Releases:
- [cilium](https://github.com/cilium/cilium-cli/releases)
- [hubble](https://github.com/cilium/hubble/releases)

#### Dashboards:
- [cilium-operator](https://grafana.com/grafana/dashboards/16612-cilium-operator/)
- [cilium-metrics](https://grafana.com/grafana/dashboards/16611-cilium-metrics/)
- [hubble-metrics](https://grafana.com/grafana/dashboards/16613-hubble/)
