---

copyright:
  years: 2025
lastupdated: "2025-11-04"

subcollection: dr-automation-powervs

keywords: add migration

---

# Additonal migration strategies
{: #add-work-load}

You can engage IBM teams and services to assist you throughout the migration lifecycle.
{:shortdesc: .shortdesc}

Expert Labs
IBM Services for Cloud Migration

## IBM cloud object storage
{: #ibm-clou-sto}

Cloud Object Storage can be used as an intermediary location to store files from your On-premises environment. You can retrieve and send your files to the Power Virtual Server environment from this location. You must create Cloud Object Storage buckets to transfer data over the public internet or privately secured links. For more information, see IBM Cloud Object Storage [FAQ](https://www.ibm.com/cloud/object-storage/faq).

To transfer data from Cloud Object Storage (COS) to an AIX virtual machine (VM) in the context of DR Automation, the KSYS orchestrator is responsible for managing data workflows. Ensure that the KSYS node is configured with AIX 7.3 or later and is connected to both the active and backup sites via HTTPS. The orchestrator uses APIs exposed by the Service Broker to retrieve VM images and configuration files stored in COS. These files are critical for initializing disaster recovery operations and maintaining consistency between sites. The COS interaction is managed securely and efficiently to ensure that the KSYS node can perform its designated tasks.

The retrieved data is automatically deployed to the target AIX VM by the KSYS orchestrator. Using pre-configured workflows, the orchestrator ensures proper placement and application of the data, eliminating the need for manual intervention. These workflows are triggered through the IBM Cloud Catalog UI, aligning with DR objectives and policies. The KSYS node verifies the consistency of data across sites, supporting seamless failover and failback operations. This automated process ensures a reliable and streamlined integration of COS into the DR Automation framework.
