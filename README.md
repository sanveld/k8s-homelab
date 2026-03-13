# k8s-homelab

Production-grade Kubernetes homelab running on Proxmox, managed with GitOps principles.

## Architecture

```
k8s-homelab/
├── cluster/
│   ├── core/              # Core platform services (ingress, cert-manager, monitoring)
│   ├── apps/              # Application workloads
│   └── infrastructure/    # GitOps engine, namespaces, RBAC
├── ansible/               # Node configuration & cluster maintenance
├── docs/                  # Architecture decisions & runbooks
└── .github/workflows/     # CI: linting, validation, security scanning
```

## Tech Stack

| Layer | Tool | Status |
|-------|------|--------|
| Hypervisor | Proxmox VE | Running |
| OS / Nodes | Ubuntu Server | Running |
| Configuration | Ansible | TODO |
| Distribution | kubeadm | Running |
| CNI | Calico | Running |
| GitOps | ArgoCD | TODO |
| Helm | Custom + upstream charts | TODO |
| Ingress | Nginx Ingress / Traefik | TODO |
| TLS | cert-manager + Let's Encrypt | TODO |
| DNS | ExternalDNS | TODO |
| Secrets | Sealed Secrets | TODO |
| Monitoring | Prometheus + Grafana | TODO |
| Logging | Loki + Promtail | TODO |
| Storage | Longhorn | TODO |
| Backup | Velero | TODO |
| Network Policies | Calico | TODO |

## Cluster

- **Control plane:** 1 node (`k8s-control`)
- **Workers:** 1 node (`k8s-worker1`)
- **Network:** 10.27.27.0/24
- **Kubeadm-managed** with Calico CNI

## Roadmap

### Phase 1: Ansible
- [ ] Inventory for Proxmox host and K8s nodes
- [ ] Playbook: OS hardening (SSH, firewall, unattended upgrades)
- [ ] Playbook: kubeadm node prerequisites (container runtime, kubelet, kubeadm)
- [ ] Playbook: cluster join/reset helpers
- [ ] Playbook: kubeconfig fetch

### Phase 2: Core Platform
- [ ] Deploy ArgoCD and configure app-of-apps pattern
- [ ] Set up ingress controller (Nginx Ingress or Traefik)
- [ ] Configure cert-manager with Let's Encrypt (staging first, then prod)
- [ ] Deploy ExternalDNS for automatic DNS record management
- [ ] Set up Sealed Secrets for secret management
- [ ] Define network policies and namespace isolation with Calico

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
- [ ] Migrate Gitea from raw manifests to Helm chart
- [ ] Implement HPA (Horizontal Pod Autoscaler) on a workload
- [ ] Add health checks, resource requests/limits, PDBs

### Phase 6: Hardening & CI
- [ ] CI pipeline: Helm lint, kubeval/kubeconform, Trivy scanning
- [ ] RBAC policies and ServiceAccount best practices
- [ ] Pod Security Standards (restricted)
- [ ] Document architecture decisions in `docs/`

## Hardware

Single Proxmox VE server (Debian 12):
- **Storage:** 2x SSDs (VMs/CTs) + 1x 3.6TB HDD (ZFS, data/backups)
- **RAM:** ~7.5 GB shared across all workloads — resource efficiency matters

## Getting Started

```bash
export KUBECONFIG=~/.kube/config-homelab
kubectl get nodes
```

## License

MIT
