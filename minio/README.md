#### Deploy to cluster:
```bash
helm repo add bitnami "https://charts.bitnami.com/bitnami" && helm repo update
```
```bash
helm upgrade --install s3 "bitnami/minio" -f values.yml -n testing --version "14.1.7"
```

#### Check updates:
```bash
helm search repo "bitnami/minio"
```

#### Get default values:
```bash
helm show values "bitnami/minio" > default-values.yml
```

#### Get manifests:
```bash
helm template s3 "bitnami/minio" -f values.yml -n testing --version "14.1.7" > manifests.yml
```

#### URLs:
- [kubernetes-example](https://min.io/docs/minio/kubernetes/upstream/)
- [containers-example](https://min.io/docs/minio/container/index.html)
- [chart](https://github.com/bitnami/charts/tree/main/bitnami/minio)
- [images](https://hub.docker.com/r/minio/minio/tags)
- [client](https://github.com/minio/minio-go)
