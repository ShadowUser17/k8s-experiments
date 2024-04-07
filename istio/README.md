#### Install:
- The minimal profile provides only `istiod`.
- Use default profile for install `istio-ingressgateway`.
```bash
curl -L "https://github.com/istio/istio/releases/download/${version}/istio-${version}-linux-amd64.tar.gz" -o istio-linux-amd64.tar.gz && \
tar -xzf istio-linux-amd64.tar.gz && rm -f istio-linux-amd64.tar.gz && ./istio-"${version}"/bin/istioctl install --verify --set profile=minimal -y
```

#### Uninstall:
```bash
istioctl uninstall --set profile=minimal --purge -y
```

#### Manual injection:
```bash
istioctl kube-inject -f ./deploy.yml | kubectl apply -f -
```
```bash
kubectl kustomize . | istioctl kube-inject -f - | kubectl apply -f -
```

#### Namespace injection:
```bash
kubectl label namespace default istio-injection=enabled --overwrite
```

#### Enable monitoring:
```bash
kubectl apply -f ./prom-operator.yml
```

#### Create IngressClass:
```bash
kubectl apply -f ./ingress-class.yml
```

#### Create Issuer:
- Warning! The `secret` for `ingress` must be in the `istio-system` namespace!
```bash
kubectl apply -f ./ingress-issuer.yml
```

#### URLs:
- [Releases](https://github.com/istio/istio/releases)
- [Documentation](https://istio.io/latest/docs/)

#### Dashboards:
- [istio-wasm-extension](https://grafana.com/grafana/dashboards/13277-istio-wasm-extension-dashboard/)
- [istio-control-plane](https://grafana.com/grafana/dashboards/7645-istio-control-plane-dashboard/)
- [istio-workload](https://grafana.com/grafana/dashboards/7630-istio-workload-dashboard/)
- [istio-service](https://grafana.com/grafana/dashboards/7636-istio-service-dashboard/)
- [istio-mesh](https://grafana.com/grafana/dashboards/7639-istio-mesh-dashboard/)
