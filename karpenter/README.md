#### Deploy to cluster:
```bash
helm upgrade --install karpenter "oci://public.ecr.aws/karpenter/karpenter" -f values.yml -n kube-system --version "0.35.4" \
--set "settings.clusterName=${CLUSTER_NAME}" --set "settings.interruptionQueue=${CLUSTER_NAME}"
```

#### Get manifests:
```bash
helm template karpenter "oci://public.ecr.aws/karpenter/karpenter" -f values.yml -n kube-system --version "0.35.4" \
--set "settings.clusterName=${CLUSTER_NAME}" --set "settings.interruptionQueue=${CLUSTER_NAME}" > manifests.yml
```

#### URLs:
- [deploy](https://karpenter.sh/v0.35/getting-started/getting-started-with-karpenter/)
- [concepts](https://karpenter.sh/v0.35/concepts/)
- [metrics](https://karpenter.sh/v0.35/reference/metrics/)
