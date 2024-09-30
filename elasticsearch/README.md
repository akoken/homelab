# Elasticsearch

## Preparation
Open your terminal and run the command down below, this will add all the repositories that we need for our Elastic stack:

```bash
# Add ELK stack helm repo
helm repo add elastic https://helm.elastic.co

# Update repository list
helm repo update

# Confirm repos are added
helm search repo elastic

# Show all values
helm show values elastic/elasticsearch > values.yml 
```

**override.yaml:**
```bash
replicas: 1
minimumMasterNodes: 1

ingress:
  enabled: false

esJavaOpts: "-Xmx1g -Xms1g"

resources:
  requests:
    cpu: "1000m"
    memory: "2Gi"
  limits:
    cpu: "1000m"
    memory: "2Gi"
```
## Installation
The following command installs only elasticsearch:

```bash
helm -n elasticsearch upgrade --install es elastic/elasticsearch --create-namespace --version 8.5.1 -f override.yaml --set secret.password=P@ssW0rd
```
> Do not forget to change the password!
