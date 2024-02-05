#### grafana-backup deploy to K8S:
```bash
kubectl apply -f grafana-backup-cronjob.yml
```
```bash
kubectl -n testing patch cronjob grafana-backup-tool -p '{"spec": {"schedule": "*/30 * * * *"}}'
```
```bash
kubectl -n testing patch cronjob grafana-backup-tool -p '{"spec": {"suspend": true}}'
```

#### grafana-backup restore manually:
```bash
python3 -m venv --upgrade-deps env && \
./env/bin/pip3 install grafana-backup
```
```bash
export VERIFY_SSL="False"
export GRAFANA_URL="https://grafana.k3s"
export GRAFANA_TOKEN="..."
```
```bash
./env/bin/grafana-backup restore ./backups/<timestamp>.tar.gz
```

#### URLs:
- [grafana-backup-tool](https://github.com/ysde/grafana-backup-tool)
- [grafana-dashboard-manager](https://github.com/esnet/gdg)
