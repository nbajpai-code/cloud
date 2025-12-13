# Azure CLI Cheat Sheet

This document serves as a quick reference for common Azure CLI (`az`) commands, focusing on authentication, resource management, compute, and storage.

## 1. Authentication & Account (`az login`, `az account`)

Connect to Azure and manage subscriptions.

| Command | Description |
| :--- | :--- |
| `az login` | Log in to Azure interactively. |
| `az account list` | List available subscriptions. |
| `az account set --subscription "[SUBSCRIPTION_ID]"` | Set the active subscription. |
| `az account show` | Show details of the current subscription. |

**Example:**
```bash
az login
az account list --output table
az account set --subscription "My Subscription"
```

## 2. Resource Groups (`az group`)

Manage containers that hold related resources.

| Command | Description |
| :--- | :--- |
| `az group list` | List all resource groups. |
| `az group create --name [RG_NAME] --location [LOCATION]` | Create a new resource group. |
| `az group delete --name [RG_NAME]` | Delete a resource group and all its resources. |

**Example:**
```bash
az group create --name MyResourceGroup --location eastus
az group list
```

## 3. Virtual Machines (`az vm`)

Manage Azure Virtual Machines.

| Command | Description |
| :--- | :--- |
| `az vm list` | List all VMs. |
| `az vm create --resource-group [RG] --name [NAME] --image [IMAGE]` | Create a new VM. |
| `az vm start --resource-group [RG] --name [NAME]` | Start a VM. |
| `az vm stop --resource-group [RG] --name [NAME]` | Stop a VM. |
| `az vm delete --resource-group [RG] --name [NAME]` | Delete a VM. |

**Example:**
```bash
az vm create --resource-group MyResourceGroup --name MyVM --image UbuntuLTS --admin-username azureuser --generate-ssh-keys
az vm list --output table
```

## 4. Storage Accounts (`az storage`)

Manage Azure Storage accounts.

| Command | Description |
| :--- | :--- |
| `az storage account list` | List storage accounts. |
| `az storage account create --name [NAME] --resource-group [RG] --location [LOC] --sku Standard_LRS` | Create a storage account. |

**Example:**
```bash
az storage account create --name mystorageacct --resource-group MyResourceGroup --location eastus --sku Standard_LRS
```

## 5. External Resources

- **Official Azure CLI Documentation**: [Microsoft Learn](https://learn.microsoft.com/en-us/cli/azure/)
- **Azure CLI Cheat Sheet**: [Microsoft Learn](https://learn.microsoft.com/en-us/cli/azure/azure-cli-configuration)
- **Azure CLI Cheat Sheet (GitHub)**: [ferhaty/azure-cli-cheatsheet](https://github.com/ferhaty/azure-cli-cheatsheet)
- **Azure Cloud Shell Commands**: [Command List](https://economize.cloud/azure-cloud-shell-cli-commands-list-cheat-sheet/)
