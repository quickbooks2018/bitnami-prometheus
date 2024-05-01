# Bitnami Prometheus

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

