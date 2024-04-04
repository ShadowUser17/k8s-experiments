#### Install to cluster:
```bash
helm repo add kyverno "https://kyverno.github.io/kyverno" && helm repo update
```
```bash
helm upgrade --install kyverno "kyverno/kyverno" -n kyverno --version "3.1.4" --create-namespace
```
```bash
helm upgrade --install kyverno-policies "kyverno/kyverno-policies" -n kyverno --version "3.1.4"
```

#### Check updates:
```bash
helm search repo "kyverno/kyverno"
```

#### Get default values:
```bash
helm show values "kyverno/kyverno" > default-values.yml
```

#### Get manifests:
```bash
helm template kyverno "kyverno/kyverno" -n kyverno --version "3.1.4" > kyverno-manifests.yml
```
```bash
helm template kyverno-policies "kyverno/kyverno-policies" -n kyverno --version "3.1.4" > kyverno-policies.yml
```

#### Install CLI:
```bash
curl -L "https://github.com/kyverno/kyverno/releases/download/v${version}/kyverno-cli_v${version}_linux_x86_64.tar.gz" -o kyverno-cli.tgz && \
tar -xzf kyverno-cli.tgz kyverno && mv ./kyverno /usr/local/bin/ && rm -f kyverno-cli.tgz
```

#### URLs:
- [kyverno-docs](https://kyverno.io/docs/introduction/)
- [kyverno-releases](https://github.com/kyverno/kyverno/releases)
- [kyverno-examples](https://github.com/kyverno/policies)
- [kyverno-chart](https://github.com/kyverno/kyverno/tree/main/charts/kyverno)
- [kyverno-policies-chart](https://github.com/kyverno/kyverno/tree/main/charts/kyverno-policies)
