#### Deploy to cluster:
```bash
helm repo add keptn "https://charts.lifecycle.keptn.sh" && helm repo update
```
```bash
helm upgrade --install keptn "keptn/keptn" -n keptn-system --create-namespace --wait
```

#### Check updates:
```bash
helm search repo "keptn/keptn"
```

#### Get default values:
```bash
helm show values "keptn/keptn" > keptn-defaults.yml
```

#### URLs:
- [Docs](https://keptn.sh/stable/docs/)
- [Chart](https://github.com/keptn/lifecycle-toolkit/tree/main/chart)
- [Releases](https://github.com/keptn/lifecycle-toolkit/releases)
