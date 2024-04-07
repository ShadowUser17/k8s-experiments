#### Deploy to cluster:
```bash
kubectl create namespace monitoring
```
```bash
helm repo add prometheus-community "https://prometheus-community.github.io/helm-charts" && helm repo update
```
```bash
helm upgrade --install prom-operator "prometheus-community/kube-prometheus-stack" -f prom-operator-values.yml -n monitoring --version "58.0.0"
```

#### Get Grafana credentials:
```bash
kubectl -n monitoring get secret prom-operator-grafana -o go-template='{{index .data "admin-user" | base64decode}}'
```
```bash
kubectl -n monitoring get secret prom-operator-grafana -o go-template='{{index .data "admin-password" | base64decode}}'
```

#### Get Alertmanager config:
```bash
kubectl -n monitoring exec -it alertmanager-prom-operator-kube-prometh-alertmanager-0 -- cat /etc/alertmanager/config_out/alertmanager.env.yaml
```

#### Get operator selectors:
```bash
kubectl -n monitoring get prometheus prom-operator-kube-prometh-prometheus -o jsonpath='{.spec.podMonitorSelector}'
```
```bash
kubectl -n monitoring get prometheus prom-operator-kube-prometh-prometheus -o jsonpath='{.spec.probeSelector}'
```
```bash
kubectl -n monitoring get prometheus prom-operator-kube-prometh-prometheus -o jsonpath='{.spec.ruleSelector}'
```
```bash
kubectl -n monitoring get prometheus prom-operator-kube-prometh-prometheus -o jsonpath='{.spec.scrapeConfigSelector}'
```
```bash
kubectl -n monitoring get prometheus prom-operator-kube-prometh-prometheus -o jsonpath='{.spec.serviceMonitorSelector}'
```
```bash
kubectl -n monitoring get alertmanager prom-operator-kube-prometh-alertmanager -o jsonpath='{.spec.alertmanagerConfigSelector}'
```

#### Check updates:
```bash
helm search repo "prometheus-community/kube-prometheus-stack"
```

#### Get default values:
```bash
helm show values "prometheus-community/kube-prometheus-stack" > default-values.yml
```

#### Get manifests:
```bash
helm template prom-operator "prometheus-community/kube-prometheus-stack" -f prom-operator-values.yml -n monitoring --version "58.0.0" > manifests.yml
```

#### Disable the next rules for EKS:
- `kubeSchedulerAlerting`
- `kubeSchedulerRecording`
- `kubeControllerManager`
- `kubeProxy`

#### URLs:
- [API](https://prometheus-operator.dev/docs/operator/api/)
- [Docs](https://prometheus-operator.dev/docs/prologue/introduction/)
- [Chart](https://github.com/prometheus-community/helm-charts/tree/main/charts/kube-prometheus-stack)
- [Releases](https://github.com/prometheus-operator/prometheus-operator/releases)
