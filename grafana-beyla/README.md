#### Deploy:
```bash
kubectl create namespace testing
```
```bash
kubectl apply -f test-app.yml
```
```bash
kubectl apply -f monitoring.yml
```

#### Access:
```bash
kubectl -n testing port-forward svc/beyla-test-app 8080
```
```bash
kubectl -n testing port-forward svc/beyla-test-app 8443
```

#### URLs:
- [Docs](https://grafana.com/docs/grafana-cloud/monitor-applications/beyla/)
- [Images](https://hub.docker.com/r/grafana/beyla/tags)
