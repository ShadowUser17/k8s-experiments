#### Install to cluster:
```bash
helm repo add elastic "https://helm.elastic.co" && helm repo update
```
```bash
helm upgrade --install elastic-operator "elastic/eck-operator" -n elastic-system --version "2.12.1" --create-namespace
```

#### Check updates:
```bash
helm search repo "elastic/eck-operator"
```

#### Get default values:
```bash
helm show values "elastic/eck-operator" > default-values.yml
```

#### Get manifests:
```bash
helm template elastic-operator "elastic/eck-operator" -n elastic-system --version "2.12.1" > manifests.yml
```

#### Get API resources:
```bash
kubectl api-resources | grep elastic
```

#### K8S:
- [operator-quickstart](https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-quickstart.html)
- [operator-upgrading](https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-upgrading-eck.html)
- [operator-config](https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-operator-config.html)
- [api-reference](https://www.elastic.co/guide/en/cloud-on-k8s/current/k8s-api-reference.html)

#### Beats:
- [Docs](https://www.elastic.co/guide/en/beats/libbeat/current/index.html)
- [Releases](https://github.com/elastic/beats/releases)

#### Kibana:
- [Docs](https://www.elastic.co/guide/en/kibana/current/index.html)
- [Images](https://hub.docker.com/_/kibana/tags)
- [Releases](https://github.com/elastic/kibana/releases)

#### Logstash:
- [Docs](https://www.elastic.co/guide/en/logstash/current/index.html)
- [Images](https://hub.docker.com/_/logstash/tags)
- [Releases](https://github.com/elastic/logstash/releases)

#### Elasticsearch:
- [API](https://www.elastic.co/guide/en/elasticsearch/reference/current/rest-apis.html)
- [Docs](https://www.elastic.co/guide/en/elastic-stack/current/index.html)
- [Images](https://hub.docker.com/_/elasticsearch/tags)
- [Releases](https://github.com/elastic/elasticsearch/releases)
