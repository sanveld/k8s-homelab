# k8s-homelab

Production-grade Kubernetes homelab running on bare metal, managed with GitOps principles.

## Architecture

```
k8s-homelab/
├── cluster/
│   ├── core/              # Core platform services (ingress, cert-manager, monitoring)
│   ├── apps/              # Application workloads
│   └── infrastructure/    # GitOps engine, namespaces, RBAC
├── terraform/             # Infrastructure provisioning
├── ansible/               # Node configuration & K8s bootstrap
├── docs/                  # Architecture decisions & runbooks
└── .github/workflows/     # CI: linting, validation, security scanning
```

## Tech Stack

| Layer | Tool | Status |
|-------|------|--------|
| OS / Nodes | Ubuntu Server | TODO |
| Provisioning | Terraform | TODO |
| Configuration | Ansible | TODO |
| Distribution | k3s | TODO |
| GitOps | ArgoCD | TODO |
| Helm | Custom + upstream charts | TODO |
| Ingress | Traefik | TODO |
| TLS | cert-manager + Let's Encrypt | TODO |
| DNS | ExternalDNS | TODO |
| Secrets | Sealed Secrets | TODO |
| Monitoring | Prometheus + Grafana | TODO |
| Logging | Loki + Promtail | TODO |
| Storage | Longhorn | TODO |
| Backup | Velero | TODO |
| Network Policies | Cilium / Calico | TODO |

## Roadmap

### Phase 1: Foundation
- [ ] Provision nodes with Terraform
- [ ] Configure nodes with Ansible (SSH hardening, packages, firewall)
- [ ] Bootstrap k3s cluster (1 server + 2 agents)
- [ ] Set up kubectl access and kubeconfig management

### Phase 2: Core Platform
- [ ] Deploy ArgoCD and configure app-of-apps pattern
- [ ] Set up Traefik ingress controller
- [ ] Configure cert-manager with Let's Encrypt (staging first, then prod)
- [ ] Deploy ExternalDNS for automatic DNS record management
- [ ] Set up Sealed Secrets for secret management
- [ ] Define network policies and namespace isolation

### Phase 3: Observability
- [ ] Deploy kube-prometheus-stack (Prometheus + Grafana)
- [ ] Set up Loki + Promtail for log aggregation
- [ ] Create Grafana dashboards for cluster health
- [ ] Configure alerting rules (node down, pod restarts, resource pressure)

### Phase 4: Storage & Backup
- [ ] Deploy Longhorn for distributed block storage
- [ ] Configure StorageClasses and PV reclaim policies
- [ ] Set up Velero for cluster backup and disaster recovery
- [ ] Test backup/restore workflow

### Phase 5: Applications
- [ ] Deploy a sample app with Helm (custom chart)
- [ ] Set up a self-hosted service (e.g., Gitea, Vaultwarden, or similar)
- [ ] Implement HPA (Horizontal Pod Autoscaler) on a workload
- [ ] Add health checks, resource requests/limits, PDBs

### Phase 6: Hardening & CI
- [ ] CI pipeline: Helm lint, kubeval/kubeconform, Trivy scanning
- [ ] RBAC policies and ServiceAccount best practices
- [ ] Pod Security Standards (restricted)
- [ ] Document architecture decisions in `docs/`

## Hardware

> TODO: Document your homelab hardware setup here.

## Getting Started

> TODO: Add bootstrap instructions once Phase 1 is complete.

## License

MIT
