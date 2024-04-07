#### Deploy to cluster:
```bash
helm repo add prometheus-community "https://prometheus-community.github.io/helm-charts" && helm repo update
```
```bash
helm upgrade --install snmp "prometheus-community/prometheus-snmp-exporter" -f values.yml -n monitoring --version "5.1.0"
```

#### Show collected data:
```
sum({job="snmp-prometheus-snmp-exporter"}) by(__name__, ifName, ifType, ifIndex, ifPhysAddress, ifDescr, ifSpecific)
```

#### Check updates:
```bash
helm search repo "prometheus-community/prometheus-snmp-exporter"
```

#### Get default values:
```bash
helm show values "prometheus-community/prometheus-snmp-exporter" > default-values.yml
```

#### Get manifests:
```bash
helm template snmp "prometheus-community/prometheus-snmp-exporter" -f values.yml -n monitoring --version "5.1.0" > manifests.yml
```

#### URLs:
- [Docs](https://github.com/prometheus/snmp_exporter/blob/main/README.md)
- [Chart](https://github.com/prometheus-community/helm-charts/tree/main/charts/prometheus-snmp-exporter)
- [Releases](https://github.com/prometheus/snmp_exporter/releases)
- [Dashboard](https://grafana.com/grafana/dashboards/11169-snmp-stats/)
