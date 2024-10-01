# Highly Available Redis

## Preparation
Open your terminal and run the command down below, this will add all the repositories that we need for Redis:

```bash
# Add Prometheus helm repo
helm repo add bitnami https://charts.bitnami.com/bitnami

# Update repository list
helm repo update

# Search helm charts and list all versions
helm search repo bitnami/redis --version

# Show all values
helm show values bitnami/redis > values.yml 
```

## Installation

```bash
helm upgrade --install redis bitnami/redis -f .\override.yaml -n redis --create-namespace
```