# Azure File Storage

1. What is it?

    Azure File Storage is a fully managed **file share service** in the cloud - Any type of files.
    It provides the Server Message Block (SMB) protocol for sharing files across applications and VMs in the Azure cloud.

2. When to use it?

    when you need a shared file system that can be accessed from multiple VMs or applications (pods).
    It is suitable for scenarios like storing configuration files, sharing file data between applications, and serving as a common storage location for applications in a cloud environment.

3. Equivalent service in AWS:

    Amazon Elastic File System (EFS). 
    
    - 1 file source multiple vm users: File System in Azure/ EFS in AWS
    - 1 file source 1 vm users: Manage Disk in Azure/ EBS in AWS

    EFS provides scalable file storage for use with Amazon EC2 instances, supporting the Network File System (NFS) protocol.