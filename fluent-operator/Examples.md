#### Get resource selectors:
```bash
kubectl get cfbc fluent-bit-config -o jsonpath='{.spec.inputSelector}' | jq
```
```bash
kubectl get cfbc fluent-bit-config -o jsonpath='{.spec.filterSelector}' | jq
```
```bash
kubectl get cfbc fluent-bit-config -o jsonpath='{.spec.outputSelector}' | jq
```

#### Required labels:
```yaml
metadata:
  labels:
    fluentbit.fluent.io/enabled: "true"
```

#### URLs:
- [Docs](https://github.com/fluent/fluent-operator/tree/master/docs)
