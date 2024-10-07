# ArgoCD

## Preparation
Argo Helm is a collection of community maintained charts for https://argoproj.github.io projects. The charts can be added using following command:

```bash
# Add ArgoCD helm repo
helm repo add argo https://argoproj.github.io/argo-helm

# Update repository list
helm repo update
```

**override.yaml:**
```bash
redis-ha:
  enabled: true

controller:
  replicas: 1

server:
  replicas: 3

repoServer:
  replicas: 3

applicationSet:
  replicas: 3

```
## Installation 
The following command installs highly available version without autoscaling.

```bash
helm search repo argo/argo-cd --versions

helm upgrade --install argocd argo/argo-cd --values .\override.yaml -n argocd --version 6.7.18 --create-namespace
```

## Access the Argo CD Server
By default, the Argo CD API server is not exposed with an external IP. To access the API server, follow the guide down below:

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443

# Retrieve the initial password
argocd admin initial-password -n argocd

# Login to the server
argocd login http://localhost:8080

# List users
argocd account list
```

## Ingress Configuration
ArgoCD API server runs both a gRPC(used by the CLI), as well as a HTTP/HTTPS server(used by the UI). Both protocols are exposed by the argocd-server service object on the following ports:
* 443 - gRPC/HTTPS
* 80 - HTTP(redirects to HTTPS)

### Nginx Ingress
```bash
kubectl apply -f .\ingress-http.yaml -n argocd
```
