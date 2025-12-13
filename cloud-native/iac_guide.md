# Infrastructure as Code (IaC) Guide

## 1. Terraform (Provisioning)
"Write, Plan, and Create Infrastructure as Code."

### Core Concepts
- **Providers**: Plugins to interact with APIs (AWS, Azure, Kubernetes).
- **State**: The source of truth for your infrastructure (`terraform.tfstate`). **Always use remote state** (S3, GCS, Terraform Cloud).
- **Modules**: Reusable containers for multiple resources.
- **HCL**: HashiCorp Configuration Language.

### Best Practices for Kubernetes
- **Separate Lifecycle**: Keep K8s *cluster* provisioning separate from *application* deployment.
- **Helm Provider**: Use the Terraform Helm provider for installing complex charts like Cert-Manager or Ingress Controllers.
- **Kubernetes Provider**: Use for defining Namespaces, StorageClasses, and RBAC via Terraform.

### Essential Resources
- [Terraform Registry](https://registry.terraform.io/)
- [Terraform Best Practices](https://www.terraform-best-practices.com/)

## 2. Ansible (Configuration Management)
"Automation for everyone."

### Core Concepts
- **Playbooks**: YAML files defining automation tasks.
- **Inventory**: List of managed nodes (hosts).
- **Roles**: Reusable units of organization (tasks, vars, files).
- **Collections**: Distribution format for Ansible content.

## 3. GitOps
"Git as the single source of truth."

- **Principles**: Declarative, Versioned, Automated, Reconciled.
- **Tools**: ArgoCD, Flux.
- **Workflow**: git push -> CI tests -> CD agent synchronizes cluster state.
