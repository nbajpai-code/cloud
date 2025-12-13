# Oracle Cloud Infrastructure (OCI) CLI Cheat Sheet

This document serves as a quick reference for common OCI CLI (`oci`) commands, focusing on configuration, compute, object storage, and networking.

## 1. Setup & Configuration (`oci setup`)

Configure the CLI and manage sessions.

| Command | Description |
| :--- | :--- |
| `oci setup config` | Interactive setup for the CLI configuration file. |
| `oci setup repair-file-permissions` | Fix file permissions for the config and key files. |
| `oci session authenticate` | Authenticate a session (e.g., for browser-based login). |

**Example:**
```bash
oci setup config
oci setup repair-file-permissions --file /Users/me/.oci/config
```

## 2. Compute Instances (`oci compute instance`)

Manage OCI Compute instances.

| Command | Description |
| :--- | :--- |
| `oci compute instance list --compartment-id [OCID]` | List instances in a compartment. |
| `oci compute instance launch --availability-domain [AD] --compartment-id [OCID] --shape [SHAPE] --subnet-id [SUBNET_OCID]` | Launch a new instance. |
| `oci compute instance action --action CHECK|STOP|START|RESET --instance-id [OCID]` | Perform power actions on an instance. |
| `oci compute instance terminate --instance-id [OCID]` | Terminate an instance. |

**Example:**
```bash
oci compute instance list --compartment-id ocid1.compartment.oc1..aaaa...
oci compute instance action --action STOP --instance-id ocid1.instance.oc1.phx.aaaa...
```

## 3. Object Storage (`oci os`)

Manage Object Storage buckets and objects.

| Command | Description |
| :--- | :--- |
| `oci os ns get` | Get the Object Storage namespace for the tenancy. |
| `oci os bucket list --compartment-id [OCID]` | List buckets in a compartment. |
| `oci os bucket create --compartment-id [OCID] --name [NAME]` | Create a new bucket. |
| `oci os object put --bucket-name [BUCKET] --file [FILE]` | Upload a file to a bucket. |
| `oci os object list --bucket-name [BUCKET]` | List objects in a bucket. |

**Example:**
```bash
oci os bucket create --compartment-id ocid1.compartment.oc1..aaaa... --name my-bucket
oci os object put --bucket-name my-bucket --file ./my-file.txt
```

## 4. Networking (`oci network`)

Manage Virtual Cloud Networks (VCNs) and subnets.

| Command | Description |
| :--- | :--- |
| `oci network vcn list --compartment-id [OCID]` | List VCNs. |
| `oci network vcn create --compartment-id [OCID] --cidr-block [CIDR]` | Create a VCN. |

**Example:**
```bash
oci network vcn list --compartment-id ocid1.compartment.oc1..aaaa...
```

## 5. External Resources

- **Official OCI CLI Documentation**: [Oracle Docs](https://docs.oracle.com/en-us/iaas/Content/API/Concepts/cliconcepts.htm)
- **OCI CLI Command Reference**: [Reference](https://docs.oracle.com/en-us/iaas/tools/oci-cli/latest/oci_cli_docs/)
- **Awesome Oracle Cloud**: [GitHub](https://github.com/oracle/awesome-oracle-cloud)
- **Awesome OCI**: [karthequian/awesome-oci](https://github.com/karthequian/awesome-oci)
