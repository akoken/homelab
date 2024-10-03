# Prometheus

## Preparation

```bash
# Add Prometheus helm repo
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts

# Update repository list
helm repo update

# Search helm charts and list all versions
helm search repo prometheus-community/kube-prometheus-stack --version

# Show all values
helm show values prometheus-community/kube-prometheus-stack > values.yml 
```

## Installation

```bash
helm upgrade --install kube-prometheus-stack prometheus-community/kube-prometheus-stack -f .\prod\override.yaml --version 58.2.2 -n monitoring --create-namespace
```
