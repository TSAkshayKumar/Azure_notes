# Azure CLI — Quick Notes (Windows)

**What:** Terminal tool to manage Azure resources (instead of Portal clicks)
**Why:** Automation + speed + fewer errors, at scale

---

## Setup
- Download & run the **MSI installer** from Microsoft (search "Install Azure CLI Windows")
- Then in Command Prompt / PowerShell:
```powershell
az version                  # check install
az login                    # connect account (opens browser)
```

## Resource Group
```powershell
az group create --name myRG --location eastus
az group delete --name myRG          # deletes everything inside too
```

## Virtual Machine
```powershell
az vm create --resource-group myRG --name myVM --image Ubuntu2204
```

## Storage Account
```powershell
az storage account create --name mystorage --resource-group myRG --location eastus --sku Standard_LRS
```

---
✅ Always `az group delete` when done testing → avoids extra billing
✅ One resource group delete = cleans up everything inside it
