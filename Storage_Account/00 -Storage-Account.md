# Azure Storage Account

## What is an Azure Storage Account?

An **Azure Storage Account** is the **top-level Azure resource** that provides a unique capabilities to store and manage data in the cloud.

Think of it as a **container for Azure storage services**. You create one Storage Account, then use it to create and manage different storage types.

**Analogy**

``` text
Storage Account (Warehouse)
├── Blob Containers (Objects)
├── File Shares
├── Queues
└── Tables
```

```text
Storage Account Blob
│
├── Container: Images
│     ├── cat.jpg
│     ├── logo.png
│
├── Container: Documents
│     ├── report.pdf
│     ├── notes.docx
│
└── Container: Videos
      ├── intro.mp4
      ├── demo.mp4
```

------------------------------------------------------------------------

## Why do we need a Storage Account?

-   Store application data
-   Store images, videos, PDFs, backups
-   Share files across machines
-   Queue messages between services. Used in Async operation. 
-   Store NoSQL key-value data in tables.
-   Integrate with other Azure AI resources like: Azure AI, Azure AI Search, Azure OpenAI, Databricks etc.

------------------------------------------------------------------------

## Storage Services

  ------------------------------------------------------------------------
  Service            Stores           Common Use Cases
  ------------------ ---------------- ------------------------------------
  Blob Storage       Objects (files)  Images, videos, PDFs, AI datasets,
                                      backups

  Azure Files        Shared files     File shared between VM and pods.

  Queue Storage      Messages         Communication between services.

  Table Storage      NoSQL key-value  Metadata, lightweight structured
                     data             data like user data.
  ------------------------------------------------------------------------


------------------------------------------------------------------------

## Storage Account Types

-   General-purpose v2 (GPv2) ⭐ Recommended
-   Premium Block Blob
-   Premium File Shares
-   Premium Page Blob

GPv2 supports almost all modern Azure storage features.

------------------------------------------------------------------------

## Performance Tiers

### Standard

-   HDD-based
-   Lower cost
-   Most workloads

### Premium

-   SSD-based
-   Low latency
-   High-performance applications

------------------------------------------------------------------------

## Access Tiers (Blob Storage)

### Hot

-   Frequently accessed
-   Highest storage cost
-   Lowest access cost

### Cool

-   Infrequently accessed
-   Lower storage cost
-   Higher access cost

### Archive

-   Rarely accessed
-   Lowest storage cost
-   Retrieval may take hours

------------------------------------------------------------------------

## Redundancy Options

Option   Copies  Protection              Example
-------- ------ -----------------        -------------------------------------------------------
LRS      3      Single datacenter          Internal application where a single datacenter is enough.
ZRS      3      Multiple zones             E-commerce website requiring high availability within 
                                           one region.
GRS      6      Secondary region           Backup or disaster recovery across two Azure regions.
GZRS     6      Zones + secondary region   Banking or mission-critical applications requiring 
                                           maximum protection.

------------------------------------------------------------------------

## Security Features

- **Microsoft Entra ID Authentication**:    Uses Azure identities (users, groups, managed identities, service principals) to securely access the storage account without sharing keys. *Recommended by Microsoft.* 

- **Shared Access Signature (SAS) Token**: Grants **temporary, limited access** to specific resources (e.g., read a blob for 1 hour) without exposing the Storage Account Key.
 
- **Storage Account Keys (Access Keys)**: Two **master keys** that provide full access to the storage account. Primarily used by backend applications or for initial setup. Avoid sharing them.

- **RBAC (Role-Based Access Control)**: Controls **who can do what** by assigning Azure roles (e.g., Reader, Contributor, Storage Blob Data Reader) to users or applications.

- **Encryption at Rest**: Azure automatically encrypts stored data using AES-256 before writing it to disk. No extra configuration is needed for basic encryption.  


## Common Concepts

### Container

Logical grouping of blobs.

### Blob

Actual stored object (image, PDF, video, etc.).

### Storage Account Key for storage account

Secret used to access the storage account. A master secret for the entire Storage Account. Provides full access (unless restricted by policies). Usually long-lived until regenerated. Should be kept secret and rarely shared.

### SAS Token for storage account

Temporary, limited access without exposing account keys. Provides only the permissions you specify. Has an expiry time (minutes, hours, or days). Safer and used to grant temporary access.

------------------------------------------------------------------------

## Pricing Factors

-   Data stored
-   Number of read/write operations
-   Data transfer
-   Redundancy option
-   Performance tier
-   Access tier

------------------------------------------------------------------------

## Best Practices

-   Use GPv2 for new projects.
-   Use Blob Storage for unstructured files.
-   Use Hot/Cool/Archive appropriately.
-   Prefer Microsoft Entra ID or SAS over account keys.
-   Enable encryption and HTTPS.
-   Choose appropriate redundancy based on business needs.

------------------------------------------------------------------------

## Quick Revision

-   Storage Account = Top-level Azure storage resource.
-   Blob = Object storage.
-   Container = Folder-like grouping of blobs.
-   GPv2 = Recommended account type.
-   Standard = HDD, Premium = SSD.
-   Hot/Cool/Archive = Access tiers.
-   LRS/ZRS/GRS/GZRS = Redundancy.
-   SAS = Temporary secure access.


### Static Website Hosting

An Azure Storage Account can also **host static websites** by using **Blob Storage's Static Website** feature. Azure serves static files directly from a special Blob container (`$web`), eliminating the need for a web server.

**How it works:**

1. Enable **Static Website** in the Storage Account.
2. Azure automatically creates a **`$web`** container.
3. Upload your static files (`index.html`, CSS, JavaScript, images) to the `$web` container.
4. Azure provides a public website URL to access your site.

**Supported files:**

* HTML
* CSS
* JavaScript
* Images and other static assets

> **Note:** Storage Accounts can host **only static content**. Server-side code (e.g., Python, Node.js, Java, .NET APIs) requires services such as Azure App Service, Azure Container Apps, or Azure Functions.


