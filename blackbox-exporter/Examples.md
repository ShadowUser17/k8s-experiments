#### Static Probe example:
```yaml
apiVersion: "monitoring.coreos.com/v1"
kind: "Probe"
metadata:
  name: "probe-testing-hosts"
  namespace: "monitoring"
  labels:
    release: "prom-operator"
spec:
  prober:
    url: "prober-prometheus-blackbox-exporter.monitoring.svc:9115"
  module: "http_2xx"
  interval: "60s"
  targets:
    staticConfig:
      static:
        - "http://testing.k3s/"
```

#### Ingress Probe example:
```yaml
apiVersion: "monitoring.coreos.com/v1"
kind: "Probe"
metadata:
  name: "probe-testing-ingress"
  namespace: "monitoring"
  labels:
    release: "prom-operator"
spec:
  prober:
    url: "prober-prometheus-blackbox-exporter.monitoring.svc:9115"
  module: "http_2xx"
  interval: "60s"
  targets:
    ingress:
      selector:
        matchLabels:
          app.kubernetes.io/name: "testing-app"
```
