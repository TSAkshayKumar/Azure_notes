# Azure Storage Account

## What is an Azure Storage Account?

It's an Azure resource to at top level to manage Storage related task. If your project is having multiple kinds of data like pdf, images, video, table.  you will create 1 storage account and within that you can manage all storage types. 

------------------------------------------------------------------------

## Q1. Why do we need a Storage Account?

-   We need something to Store application data
-   It Store varities like images, videos, PDFs, backups
-   Can make is as single source to access data for different virtual machines.
-   It has Queue which helps you to queue messages. This helps service to perform Asyn operation.
-   It has table to Store NoSQL key-value data.
-   Integrate with other Azure AI resources like: Azure AI, Azure AI Search, Azure OpenAI, Databricks etc.

------------------------------------------------------------------------

## Storage Services

 **Following Types of sub function present within SA that helps you to handle different kinds of data:**

  ``` text
  Storage Account (Warehouse)
  ├── Blob Containers (Objects)
  ├── File Shares
  ├── Queues
  └── Tables
  ```
 
  ------------------------------------------------------------------------
  Service            Stores           Common Use Cases
  ------------------ ---------------- ------------------------------------
  Blob Storage       Objects (files)  Images, videos, PDFs, AI datasets,
                                      backups

  Azure Files        Shared files     File shared between VM and pods.

  Queue Storage      Messages         you can use it as a resource to 
                                      communicate between services

  Table Storage      NoSQL key-value  Metadata or lightweight structured
                     data             data like user data.
  ------------------------------------------------------------------------


  **Main for me will be Blob Storage**


  ```text
  Storage Account Blob (we will be going to mostly use)
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

## Quick Revision

-   Storage Account = Top-level Azure storage resource.
-   Blob = Object storage.
-   Container = Folder for grouping of blobs.
-   GPv2 = Recommended storage account type.
-   Performance tier: Standard = HDD, Premium = SSD.
-   storage account also help use to host static web pages easily.
-   Hot/Cool/Archive = Access tiers.
-   LRS/ZRS/GRS/GZRS = Redundancy.
-   Security: SAS = Temporary secure access.
-   Security: Prefer Microsoft Entra ID or SAS over account keys.
-   Security: Enable encryption and HTTPS.

------------------------------------------------------------------------

# ====================== Extra Information ================================

------------------------------------------------------------------------

## Storage Account Types 

-   General-purpose v2 (GPv2) ⭐ Recommended
-   Premium Block Blob
-   Premium File Shares
-   Premium Page Blob

GPv2 supports almost all modern Azure storage features.

------------------------------------------------------------------------

## Performance Tiers config

### Standard :
    - HDD-based , Lower cost.

### Premium:
    -   SSD-based  ,  Low latency , for High-performance applications

------------------------------------------------------------------------

## Access Tiers config (Blob Storage)

### Hot
    -   Frequently accessed data  ,   Highest storage cost  ,  Lowest access cost

### Cool
    -  Infrequently accessed data ,   Lower storage cost    ,  Higher access cost

### Archive
    -   Rarely accessed  ,   Lowest storage cost   ,   Retrieval may take hours

------------------------------------------------------------------------

## Redundancy/Backup Options configuration:

```text
Example 

Option   Copies  Protection                  Easy to remember
-------- ------  -------------------------  -----------------------------------------
LRS      3       Same datacenter            One building (internal application)
ZRS      3       3 zones but 1 region       Same city, different buildings (E-commerce)
GRS      6       2 region                   Another city / region (backup)
GZRS     6       Zones + another region     Best protection (Banking)
```

- **LRS** → Azure stores **3 copies** of your data in the **same datacenter**.

- **ZRS** → Store **1 copy in each of 3 different Zones** but **same region**. If one zone goes down, the other two still there.   

- **GRS** → stores in **2 Regions** how -> **3 copies in primary region (using LRS - 1datacenter)**, then replicates those **3 copies to a paired secondary region (using LRS)**, for region outage protection.
 
- **GZRS** → Same as GRS but here instead of **(LRS - 1 datacenter -> ZRS - 3 different zone in both regions)** is used.
- 
------------------------------------------------------------------------

## Security Features config:

- **Microsoft Entra ID Authentication**:    ***Uses Azure identities*** (users, groups, managed identities, service principals) to access storage account without sharing keys. *Recommended by Microsoft.* 

- **Shared Access Signature (SAS) Token**: Grants **temporary, limited access** (e.g., read a blob for 1 hour) without exposing the Storage Account Key.
 
- **Storage Account Keys (Access Keys)**: Two **master keys** that provide full access to the storage account. Primarily used by backend applications or for initial setup. Avoid sharing them.

- **RBAC (Role-Based Access Control)**: Controls **who can do what** by assigning Azure roles (e.g., Reader, Contributor, Storage Blob Data Reader) to users or applications.

- **Encryption at Rest**: Azure automatically encrypts stored data using AES-256 before writing it to disk. No extra configuration is needed for basic encryption.  

------------------------------------------------------------------------

## Common Concepts

### Container

Logical grouping of blobs.

### Blob

It stores object files (image, PDF, video, etc.).

### Storage Account Key for storage account

Secret used to access the storage account. Provides full access (unless restricted by policies). Usually long-lived until regenerated. Should be kept secret and rarely shared. (Not a good practice to share it.)

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

## Static Website Hosting

An Azure Storage Account can also **host static websites** by using **Blob Storage's Static Website** feature.

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


