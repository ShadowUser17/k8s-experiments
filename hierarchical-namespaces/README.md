#### Create sub namespace:
```yaml
apiVersion: "hnc.x-k8s.io/v1alpha2"
kind: "SubnamespaceAnchor"
metadata:
  name: "sub-testing-sn"
  namespace: "testing"
```

#### Get sub namespaces:
```bash
kubectl get subns -A
```

#### Get cluster-wide configuration:
```bash
kubectl get hncconfiguration config -o yaml
```

#### URLs:
- [Docs](https://github.com/kubernetes-sigs/hierarchical-namespaces/blob/master/README.md)
- [Releases](https://github.com/kubernetes-sigs/hierarchical-namespaces/releases)
