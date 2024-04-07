#### ServiceMonitor example:
```yaml
apiVersion: "monitoring.coreos.com/v1"
kind: "ServiceMonitor"
metadata:
  name: "gateway"
  namespace: "monitoring"
  labels:
    release: "prom-operator"
spec:
  selector:
    matchLabels:
      app.kubernetes.io/name: "prometheus-snmp-exporter"
  endpoints:
    - port: "http"
      path: "/snmp"
      interval: "30s"
      honorLabels: true
      scrapeTimeout: "10s"
      params:
        auth: ["public_v2"]
        module: ["if_mib"]
        target: ["192.168.56.1"]
      metricRelabelings:
        - sourceLabels: ["instance"]
          targetLabel: "instance"
          replacement: "192.168.56.1"
          action: "replace"
```
