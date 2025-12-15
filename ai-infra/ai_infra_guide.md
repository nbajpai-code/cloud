# AI Infrastructure Guide

## 1. The Intersection of AI and Cloud Native
Modern AI infrastructure leverages Kubernetes for scalability, portability, and resource management (GPUs/TPUs).

## 2. Ray Framework
"Universal API for distributed computing."

### Architecture
- **Worker Nodes**: Execute tasks and actors.
- **Head Node**: Coordination (GCS - Global Control Store) and Dashboard.
- **Ray Cluster**: A collection of head and worker nodes.

### Use Cases
- **Ray Train**: Distributed training (PyTorch/TensorFlow).
- **Ray Serve**: Scalable model serving.
- **Ray Data**: Scalable datasets for ML.

## 3. KubeRay (Ray on Kubernetes)
The standard operator for managing Ray applications on Kubernetes.

### Architecture
1.  **KubeRay Operator**: A K8s pod that manages Ray Custom Resources.
2.  **CRDs (Custom Resource Definitions)**:
    - `RayCluster`: Deployment of a Ray cluster (Head + Workers).
    - `RayJob`: Orchestrates a run-to-completion job (submission -> execution -> shutdown).
    - `RayService`: Manages highly available Ray Serve applications (zero-downtime upgrades).

### Reference Architecture Flow
`Terraform` -> `EKS/GKE` -> `KubeRay Operator` -> `RayCluster CRD` -> `AI Workload`

## 4. Operational Best Practices
- **Autoscaling**: Configure Kubernetes Cluster Autoscaler alongside Ray Autoscaler.
- **GPU Scheduling**: Use Managed Node Groups with Taints/Tolerations to ensure AI workloads land on GPU nodes.
- **Multi-Tenancy**: Use K8s Namespaces and Resource Quotas to isolate Ray clusters.
- **Observability**: Integrate Ray Dashboard with Prometheus/Grafana.

## 5. Resources
- [Ray.io Documentation](https://docs.ray.io/en/latest/)
- [KubeRay GitHub](https://github.com/ray-project/kuberay)
- [Anyscale (Managed Ray)](https://www.anyscale.com/)
- [CNCF Cloud Native AI Whitepaper](https://tag-runtime.cncf.io/wgs/cncf-ai-working-group/)
- [Scaling AI wirh Ray](https://github.com/debnsuma/vhol-ray-data)
