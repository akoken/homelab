# Cilium
Cilium is an open source, cloud native solution for providing, securing, and observing network connectivity between workloads, fueled by the revolutionary Kernel technology eBPF.

## Nginx Ingress Configuration for Hubble UI
Hubble is a fully distributed networking and security observability platform for cloud native workloads. It is built on top of Cilium and eBPF to enable deep visibility into the communication and behavior of services as well as the networking infrastructure in a completely transparent manner.

```bash
# Change context to the prod cluster
kubectx np

# Apply ingress configuration
kubectl apply -f .\ingress-hubble.yaml -n argocd
```
