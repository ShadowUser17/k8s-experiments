#### Deploy Elasticsearch:
```bash
kubectl apply -f es-deploy.yml
```
```bash
kubectl get elasticsearch -n monitoring
```
```bash
kubectl -n monitoring get secret es-es-elastic-user -o go-template='{{.data.elastic | base64decode}}'
```
```bash
kubectl -n monitoring port-forward svc/es-es-http 9200
```
```bash
curl -u "elastic:${PASSWORD}" -k "https://localhost:9200/_cat/indices"
```

#### Deploy Kibana:
```bash
kubectl apply -f kb-deploy.yml
```
```bash
kubectl get kibana -n monitoring
```
```bash
kubectl -n monitoring port-forward svc/kibana-kb-http 5601
```
