#### Install to cluster:
```bash
helm repo add bitnami "https://charts.bitnami.com/bitnami" && helm repo update
```
```bash
kubectl create namespace testing
```
```bash
helm upgrade --install cache "bitnami/redis" -f ./values/redis.yml -n testing --version "19.0.2"
```

#### Check updates:
```bash
helm search repo "bitnami/redis"
```

#### Get default values:
```bash
helm show values "bitnami/redis" > redis-default.yml
```

#### Export manifests:
```bash
helm template cache "bitnami/redis" -f ./values/redis.yml -n testing --version "19.0.2" > redis-manifests.yml
```

#### Delete volumes:
```bash
kubectl delete pvc -n testing -l 'app.kubernetes.io/name=redis'
```

#### URLs:
- [Docs](https://redis.io/docs/)
- [Chart](https://github.com/bitnami/charts/tree/main/bitnami/redis)
- [Images](https://hub.docker.com/r/bitnami/redis/tags)
- [Releases](https://github.com/redis/redis/releases)
