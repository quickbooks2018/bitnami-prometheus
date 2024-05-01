# Bitnami Prometheus

# Helm Chart for Prometheus

```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo update
helm repo ls
helm search repo bitnami/prometheus --versions
helm show values bitnami/prometheus --version 1.0.6
helm show values bitnami/prometheus --version 1.0.6 > prometheus-values.yaml
helm -n monitoring upgrade --install prometheus bitnami/prometheus --version 1.0.6 -f prometheus-values.yaml --wait
helm -n monitoring upgrade --install prometheus bitnami/prometheus --version 1.0.6 --wait
```