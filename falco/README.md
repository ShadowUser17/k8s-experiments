#### Deploy to cluster:
```bash
helm repo add falco "https://falcosecurity.github.io/charts" && helm repo update
```
```bash
kubectl create namespace falcosecurity
```
```bash
helm upgrade --install falco "falco/falco" -f falco-values.yml -n falcosecurity --version "4.2.5"
```
```bash
helm upgrade --install falco-exporter "falco/falco-exporter" -f falco-exporter-values.yml -n falcosecurity --version "0.9.11"
```

#### Check updates:
```bash
helm search repo "falco/falco"
```
```bash
helm search repo "falco/falco-exporter"
```

#### Get default values:
```bash
helm show values "falco/falco" > falco-defaults.yml
```
```bash
helm show values "falco/falco-exporter" > falco-exporter-defaults.yml
```

#### falco:
- [Docs](https://falco.org/docs/)
- [Chart](https://github.com/falcosecurity/charts/tree/master/charts/falco)
- [Releases](https://github.com/falcosecurity/falco/releases)

#### falco-exporter:
- [Docs](https://github.com/falcosecurity/falco-exporter/blob/master/README.md)
- [Chart](https://github.com/falcosecurity/charts/tree/master/charts/falco-exporter)
- [Releases](https://github.com/falcosecurity/falco-exporter/releases)
