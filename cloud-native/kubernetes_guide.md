# Kubernetes & Cloud Native Guide

## 1. Core Concepts
- **Control Plane**: API Server, etcd, Scheduler, Controller Manager.
- **Workloads**: Pods, Deployments, StatefulSets, DaemonSets, Jobs.
- **Networking**: Services (ClusterIP, NodePort, LoadBalancer), Ingress, Network Policies.
- **Storage**: StorageClass, PVC, PV, CSI (Container Storage Interface).

## 2. Kubernetes Distributions
### Public Cloud (Managed)
- **AWS EKS**: Elastic Kubernetes Service. Deep integration with AWS IAM/VPC.
- **Google GKE**: Google Kubernetes Engine. The "standard" for managed K8s.
- **Azure AKS**: Azure Kubernetes Service. Tight Azure AD integration.
- **OCI OKE**: Oracle Container Engine for Kubernetes.

### Private/Edge (Self-Managed)
- **K3s**: Lightweight Kubernetes. Great for edge, CI/CD, and ARM.
- **RKE2**: Rancher Kubernetes Engine (Gov/Security focused).
- **OpenShift**: Red Hat's enterprise Kubernetes platform.

## 3. Essential Tooling
- **kubectl**: CLI for interacting with the cluster.
    - [Cheatsheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)
- **Helm**: The package manager for Kubernetes.
    - [Artifact Hub](https://artifacthub.io/)
- **Kustomize**: Template-free, declarative configuration customization.
- **ArgoCD**: GitOps continuous delivery tool.

## 4. CNCF Landscape
- **Orchestration**: Kubernetes.
- **Service Mesh**: Istio, Linkerd.
- **Observability**: Prometheus (Metrics), Grafana (Dashboard), Jaeger (Tracing).
- **Security**: OPA/Gatekeeper (Policy), Falco (Runtime security).
