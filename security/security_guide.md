# Cloud Security Guide

This guide provides a comprehensive overview of security services, best practices, and certifications for both Public and Private cloud environments.

## 1. General Concepts
- **Shared Responsibility Model**: Security *of* the cloud (Provider) vs. Security *in* the cloud (Customer).
- **Zero Trust**: "Never trust, always verify." Identity as the new perimeter.
- **Micro-segmentation**: Isolating workloads to limit lateral movement.
- **CSA Certifications**:
    - **[CCSK](https://cloudsecurityalliance.org/education/ccsk)** (Certificate of Cloud Security Knowledge): Vendor-neutral fundamentals.
    - **[CCAK](https://cloudsecurityalliance.org/education/ccak)** (Certificate of Cloud Auditing Knowledge): Auditing cloud systems.

### Essential Resources
- [CSA Cloud Controls Matrix (CCM)](https://cloudsecurityalliance.org/research/cloud-controls-matrix)
- [Awesome Cloud Security](https://github.com/4ndersonLin/awesome-cloud-security) - Curated list of security tools and resources.
- [Cloud Security Wiki](https://cloudsec.wiki/)

---

## 2. Public Cloud Security

### Amazon Web Services (AWS)
- **Identity**: [AWS IAM](https://aws.amazon.com/iam/) (Policy-based access), [IAM Identity Center](https://aws.amazon.com/iam/identity-center/).
- **Infrastructure**: [AWS Shield](https://aws.amazon.com/shield/) (DDoS), WAF, [VPC Security Groups](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html).
- **Data Protection**: [AWS KMS](https://aws.amazon.com/kms/) (Key Management), [Macie](https://aws.amazon.com/macie/) (Sensitive data discovery).
- **Monitoring**: [GuardDuty](https://aws.amazon.com/guardduty/) (Threat detection), [Security Hub](https://aws.amazon.com/security-hub/).
- **Resources**:
    - [AWS Security Documentation](https://aws.amazon.com/security/details/)
    - [AWS Well-Architected Security Pillar](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html)
    - [toniblyx/my-arsenal-of-aws-security-tools](https://github.com/toniblyx/my-arsenal-of-aws-security-tools)

### Microsoft Azure
- **Identity**: [Microsoft Entra ID](https://www.microsoft.com/en-us/security/business/identity-access/microsoft-entra-id) (formerly Azure AD), [PIM](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure).
- **Infrastructure**: [Azure DDoS Protection](https://azure.microsoft.com/en-us/products/ddos-protection/), Azure Firewall, NSGs.
- **Data Protection**: [Azure Key Vault](https://azure.microsoft.com/en-us/products/key-vault/), Information Protection.
- **Monitoring**: [Microsoft Defender for Cloud](https://azure.microsoft.com/en-us/products/defender-for-cloud/), [Microsoft Sentinel](https://azure.microsoft.com/en-us/products/microsoft-sentinel/) (SIEM).
- **Resources**:
    - [Azure Security Documentation](https://learn.microsoft.com/en-us/azure/security/)
    - [Azure Security Benchmark](https://learn.microsoft.com/en-us/security/benchmark/azure/overview)

### Google Cloud Platform (GCP)
- **Identity**: [Cloud IAM](https://cloud.google.com/iam), [BeyondCorp](https://cloud.google.com/beyondcorp) (Zero Trust).
- **Infrastructure**: [Cloud Armor](https://cloud.google.com/security/products/armor) (DDoS/WAF), [VPC Service Controls](https://cloud.google.com/vpc-service-controls).
- **Data Protection**: [Cloud KMS](https://cloud.google.com/security-key-management), Secret Manager.
- **Monitoring**: [Security Command Center](https://cloud.google.com/security-command-center), [Chronicle](https://cloud.google.com/chronicle).
- **Resources**:
    - [GCP Security Documentation](https://cloud.google.com/security/docs)
    - [Google Cloud Architecture Framework: Security](https://cloud.google.com/architecture/framework/security)

### Oracle Cloud Infrastructure (OCI)
- **Identity**: [OCI IAM](https://docs.oracle.com/en-us/iaas/Content/Identity/home.htm).
- **Infrastructure**: [Security Lists](https://docs.oracle.com/en-us/iaas/Content/Network/Concepts/securitylists.htm), NSGs.
- **Data Protection**: [OCI Vault](https://docs.oracle.com/en-us/iaas/Content/KeyManagement/Concepts/keyoverview.htm), Bastion.
- **Monitoring**: [Cloud Guard](https://docs.oracle.com/en-us/iaas/Cloud-Guard/Concepts/cloudguard_overview.htm), [Security Zones](https://docs.oracle.com/en-us/iaas/security-zone/home.htm).
- **Resources**:
    - [OCI Security Guide](https://docs.oracle.com/en-us/iaas/Content/Security/Concepts/securityoverview.htm)

---

## 3. Private Cloud Security

### VMware
- **Network Security**: [NSX](https://www.vmware.com/products/nsx.html) (Distributed Firewall, Micro-segmentation).
- **Endpoint Protection**: [Carbon Black Workload](https://www.vmware.com/products/carbon-black-workload.html).
- **Compliance**: [vRealize Operations](https://www.vmware.com/products/vrealize-operations.html) (Configuration & Compliance).
- **Resources**:
    - [VMware Security Configuration Guides](https://core.vmware.com/security-configuration-guide)
    - [VMware Security Hardening Guides](https://www.vmware.com/security/hardening-guides.html)

### OpenStack
- **Identity**: [Keystone](https://docs.openstack.org/keystone/latest/) (Authentication & Authorization).
- **Secrets Management**: [Barbican](https://docs.openstack.org/barbican/latest/) (Key management).
- **Network Security**: [Neutron](https://docs.openstack.org/neutron/latest/) (Security Groups, FWaaS).
- **Resources**:
    - [OpenStack Security Guide](https://docs.openstack.org/security-guide/)
    - [OpenStack Hardening Standards](https://docs.openstack.org/security-guide/introduction/hardening-standards.html)

### Nutanix
- **Network Security**: [Flow](https://www.nutanix.com/products/flow) (Application-centric micro-segmentation).
- **Compliance**: [Security Central](https://www.nutanix.com/products/security-central).
- **Platform**: [AOS Security](https://www.nutanix.com/products/aos/security).
- **Resources**:
    - [Nutanix Bible - Security](https://nutanixbible.com/#anchor-security)
    - [Nutanix Security Guide](https://portal.nutanix.com/page/documents/details?targetId=Nutanix-Security-Guide-v6_5:Nutanix-Security-Guide-v6_5)
