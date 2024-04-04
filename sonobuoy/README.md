#### Install CLI:
```bash
curl -L "https://github.com/vmware-tanzu/sonobuoy/releases/download/v${version}/sonobuoy_${version}_linux_amd64.tar.gz" -o sonobuoy_linux.tgz && \
tar -xzf sonobuoy_linux.tgz sonobuoy && mv ./sonobuoy /usr/local/bin/ && rm -f ./sonobuoy_linux.tgz
```

#### Run test:
```bash
sonobuoy run --wait
```

#### Run quick test:
```bash
sonobuoy run --mode quick --wait
```

#### Get results:
```bash
sonobuoy retrieve -f ./sonobuoy_results.tgz && \
sonobuoy results ./sonobuoy_results.tgz
```

#### Delete from cluster:
```bash
sonobuoy delete --wait
```

#### URLs:
- [Documentation](https://sonobuoy.io/docs/main/)
- [Releases](https://github.com/vmware-tanzu/sonobuoy/releases)
