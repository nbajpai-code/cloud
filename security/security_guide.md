# Cloud Security Guide

This guide provides a comprehensive overview of security services, best practices, and certifications for both Public and Private cloud environments.

## 1. General Concepts
- **Shared Responsibility Model**: Security *of* the cloud (Provider) vs. Security *in* the cloud (Customer).
- **Zero Trust**: "Never trust, always verify." Identity as the new perimeter.
- **Micro-segmentation**: Isolating workloads to limit lateral movement.
- **CSA Certifications**:
    - **CCSK** (Certificate of Cloud Security Knowledge): Vendor-neutral fundamentals.
    - **CCAK** (Certificate of Cloud Auditing Knowledge): Auditing cloud systems.

---

## 2. Public Cloud Security

### Amazon Web Services (AWS)
- **Identity**: AWS IAM (Policy-based access), IAM Identity Center.
- **Infrastructure**: AWS Shield (DDoS), WAF, VPC Security Groups.
- **Data Protection**: AWS KMS (Key Management), Macie (Sensitive data discovery).
- **Monitoring**: GuardDuty (Threat detection), Security Hub (Central dashboard).

### Microsoft Azure
- **Identity**: Microsoft Entra ID (formerly Azure AD), PIM (Privileged Identity Management).
- **Infrastructure**: Azure DDoS Protection, Azure Firewall, NSGs.
- **Data Protection**: Azure Key Vault, Information Protection.
- **Monitoring**: Microsoft Defender for Cloud, Microsoft Sentinel (SIEM).

### Google Cloud Platform (GCP)
- **Identity**: Cloud IAM, BeyondCorp (Zero Trust implementation).
- **Infrastructure**: Cloud Armor (DDoS/WAF), VPC Service Controls.
- **Data Protection**: Cloud KMS, Secret Manager.
- **Monitoring**: Security Command Center (SCC), Chronicle (Security Analytics).

### Oracle Cloud Infrastructure (OCI)
- **Identity**: OCI IAM (Identity Domains).
- **Infrastructure**: Security Lists, Network Security Groups (NSGs).
- **Data Protection**: OCI Vault, Bastion Service.
- **Monitoring**: Cloud Guard (CSPM), Security Zones (Enforced policy).

---

## 3. Private Cloud Security

### VMware
- **Network Security**: **NSX** (Distributed Firewall, Micro-segmentation).
- **Endpoint Protection**: Carbon Black Workload.
- **Compliance**: vRealize Operations (Configuration & Compliance).

### OpenStack
- **Identity**: **Keystone** (Authentication & Authorization).
- **Secrets Management**: **Barbican** (Key management).
- **Network Security**: **Neutron** (Security Groups, FWaaS).

### Nutanix
- **Network Security**: **Flow** (Application-centric micro-segmentation).
- **Compliance**: **Security Central** (Security posture monitoring).
- **Platform**: AOS Security Technical Implementation Guide (STIG) baseline.
