# Azure Blob Storage

1. What is it?

    Azure Blob Storage is a cloud-based **object storage** solution.
    Used to store and manage large amounts of unstructured data, such as documents, images, videos, and other types of binary and text data.
    Blobs are organized into containers, and each blob is assigned a unique URL for access.

2.  what is Object storage?

    An Object Storage stores data as objects instead of files or database records.

3. When to use it?

    Use Azure Blob Storage when you need to store and retrieve large amounts of unstructured data.
    like serving images or videos to a website, storing backups, and handling data for analytics and big data processing.

4. Example from DevOps Engineer point of view?

    A DevOps engineer may use Azure Blob Storage to store artifacts and binaries produced during the build process, ensuring a centralized and scalable storage solution.

5. Equivalent service in AWS:

    Amazon Simple Storage Service (S3).

 ------------------------------------------------------------------------
## Quick Revision
- **Blob Storage** = Azure's **Object Storage** service.
- **Object** = Any unstructured file (PDF, Image, Video, ZIP, JSON, etc.).
- **Container** = grouping of blobs.
- **Blob Types**:
  - **Block Blob** = Documents, images, videos (Most common ⭐)
  - **Append Blob** = Logs
  - **Page Blob** = Azure VM disks (VHDs)
   
- **Hot/Cool/Archive** = Access tiers based on usage frequency.
- **Every Blob has a unique URL** for access.
- **Lifecycle Management** = Automatically move Hot → Cool → Archive or delete old blobs to reduce cost.
- **Upload Methods** = Azure Portal, Storage Explorer, Azure CLI, Azure SDKs.
- **AWS Equivalent** = Amazon S3.

 ------------------------------------------------------------------------


# ========================== Extra Config Relate information ==========================

 ------------------------------------------------------------------------

## 2. Blob Types

  -----------------------------------------------------------------------
  Blob Type        Description                     Use Case
  ---------------------- ------------------------ --------------------
  Block Blob ⭐   Stores text/files in blocks      Documents, images, videos, AI datasets

  Append Blob     Optimized for append operations  Logs, telemetry                  

  Page Blob       Random read/write pages          Azure VM disks(VHDs)
 -----------------------------------------------------------------------

## 3. Access Tiers

  Tier      Best For                Storage Cost   Access Cost
  --------- ----------------------- -------------- --------------------------------
  Hot       Frequently accessed     High           Low
  Cool      Occasionally accessed   Lower          Higher
  Archive   Rarely accessed         Lowest         Highest (rehydration required)

 ------------------------------------------------------------------------


## 4. Blob URL - Each Blob has a unique url.
    https://<storage-account>.blob.core.windows.net/<container>/<blob>

Example:

    https://mystorage.blob.core.windows.net/documents/report.pdf


------------------------------------------------------------------------

## 5. Upload Options

-   Azure Portal
-   Azure Storage Explorer
-   Azure CLI
-   Azure SDKs (.NET, Python, Java, JS)
   
------------------------------------------------------------------------

## 6. Lifecycle Management

Automatically move blobs: 
- Hot → Cool 
- Cool → Archive 
- Delete after retention period

Useful for cost optimization.

------------------------------------------------------------------------

## 7. Common CLI

``` bash
az storage blob upload
az storage blob download
az storage blob list
az storage container create
```

------------------------------------------------------------------------
