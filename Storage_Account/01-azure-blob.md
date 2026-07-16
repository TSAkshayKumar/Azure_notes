# Azure Blob Storage

1. What is it?

    Azure Blob Storage is a cloud-based object storage solution provided by Microsoft Azure.
    It is designed to store and manage large amounts of unstructured data, such as documents, images, videos, and other types of binary and text data.
    Blobs are organized into containers, and each blob is assigned a unique URL for access.

- Object storage account?

    An Object Storage Account is a cloud storage service that stores data as objects instead of files or database records.

2. When to use it?

    Use Azure Blob Storage when you need to store and retrieve large amounts of unstructured data.
    It is suitable for scenarios like serving images or videos to a website, storing backups, and handling data for analytics and big data processing.

3. Example from DevOps Engineer point of view?

    A DevOps engineer may use Azure Blob Storage to store artifacts and binaries produced during the build process, ensuring a centralized and scalable storage solution.
    Azure Storage Explorer or Azure CLI can be used to automate the uploading and retrieval of artifacts during deployment pipelines.

4. Equivalent service in AWS:

    The equivalent service in AWS is Amazon Simple Storage Service (S3). S3 is also an object storage service designed for scalable and secure storage of objects, such as files and data.

 ------------------------------------------------------------------------

## 2. Blob Types

  -----------------------------------------------------------------------
  Blob Type              Description                 Use Case
  ---------------------- --------------------------- --------------------
  Block Blob ⭐          Stores text/files in blocks Documents, images,
                                                     videos, AI datasets

  Append Blob            Optimized for append        Logs, telemetry
                         operations                  

  Page Blob              Random read/write pages     Azure VM disks
                                                     (VHDs)
 -----------------------------------------------------------------------

## 3. Access Tiers

  Tier      Best For                Storage Cost   Access Cost
  --------- ----------------------- -------------- --------------------------------
  Hot       Frequently accessed     High           Low
  Cool      Occasionally accessed   Lower          Higher
  Archive   Rarely accessed         Lowest         Highest (rehydration required)

 ------------------------------------------------------------------------


## 4. Blob URL
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

Automatically move blobs: - Hot → Cool - Cool → Archive - Delete after
retention period

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
