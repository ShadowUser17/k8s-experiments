#### Create certificate:
```yaml
apiVersion: "cert-manager.io/v1"
kind: "Issuer"
metadata:
  name: "testing-issuer"
  namespace: "testing"
spec:
  selfSigned: {}
```
```yaml
apiVersion: "cert-manager.io/v1"
kind: "Certificate"
metadata:
  name: "testing-ing-cert"
  namespace: "testing"
spec:
  dnsNames: ["testing.k3s"]
  secretName: "testing-ing-cert"
  issuerRef:
    kind: "Issuer"
    name: "testing-issuer"
```

#### Ingress annotations:
```yaml
annotations:
  cert-manager.io/cluster-issuer: "k8s-cluster-issuer"
```
```yaml
annotations:
  cert-manager.io/inject-ca-from: "testing/testing-certs"
```
