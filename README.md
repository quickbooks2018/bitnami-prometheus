# Bitnami Prometheus

- https://www.youtube.com/watch?v=LUPNpQXRKB4&t=3s

# Helm Chart for Bitnami Prometheus

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
helm repo ls
helm search repo bitnami/kube-prometheus --versions
helm show values bitnami/kube-prometheus --version 9.0.5
helm show values bitnami/kube-prometheus --version 9.0.5 > prometheus-values.yaml
helm -n monitoring upgrade --install prometheus bitnami/kube-prometheus --create-namespace --version 9.0.5 -f prometheus-values.yaml --wait
helm -n monitoring upgrade --install prometheus bitnami/kube-prometheus --create-namespace --version 9.0.5 --wait

git clone https://github.com/GoogleCloudPlatform/bank-of-anthos.git
cd bank-of-anthos/

helm -n monitoring upgrade --install prometheus bitnami/kube-prometheus --create-namespace --version 9.0.5 --values extras/prometheus/oss/values.yaml --wait
```

- Configure Slack (Sample App by Google)
```bash
kubectl -n monitoring create secret generic alertmanager-slack-webhook --from-literal webhookURL=SLACK_WEBHOOK_URL

kubectl  -n monitoring kubectl apply -f extras/prometheus/oss/alertmanagerconfig.yaml
```

- Configure Prometheus
```bash
kubectl -n monitoring apply -f extras/prometheus/oss/probes.yaml
kubectl -n monitoring apply -f extras/prometheus/oss/rules.yaml
```

# Helm Chart for Bitnami Grafana

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
helm repo ls
helm search repo bitnami/grafana --versions
helm show values bitnami/grafana --version 10.0.9
helm show values bitnami/grafana --version 10.0.9 > grafana-values.yaml
helm -n monitoring upgrade --install grafana bitnami/grafana --create-namespace --version 10.0.9 -f grafana-values.yaml --wait
helm -n monitoring upgrade --install grafana bitnami/grafana --create-namespace --version 10.0.9 --wait
```

- Slack APP Creation https://api.slack.com/apps
```bash
https://api.slack.com/apps
```

- Steps to Install Addtional Scrape Configurations

- Step 1
```bash
k apply -f prometheus-additional-scrape-configs.yaml
```

- Step 2
```bash
helm -n monitoring upgrade --install prometheus bitnami/kube-prometheus --create-namespace --version 9.0.5 -f prometheus-values.yaml --wait
```

- Step 3
```bash
k apply -f additional-scrape-configs.yaml
k apply -f custom-rules.yaml
```

- Step 4
```bash
kubectl delete pod -l app.kubernetes.io/name=prometheus -n monitoring
kubectl delete pod -l app.kubernetes.io/name=alertmanager -n monitoring
```

- https://github.com/bitnami/charts/blob/main/bitnami/kube-prometheus/values.yaml