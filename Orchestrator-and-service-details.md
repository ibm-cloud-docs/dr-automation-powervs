---
copyright:
  years: 2025
lastupdated: "2025-10-09"

subcollection: dr-automation

keywords: Orchestrator details, Service details, GRS, global replication services pair
---

# Orchestrator and service details
{: #or-ser-de}

 The **Orchestrator Details** and **Service Details** sections provide comprehensive technical insights that help administrators and cloud engineers monitor and manage disaster recovery automation for their infrastructure.
 
## Orchestrator details
{: #orc-det}

**Update API Key**:

Once the deployment is successful, the **Update API Key** option is enabled. Update the API key and reuse the same key for future actions.

**DR Orchestrator name**:

The unique identifier for the primary orchestrator instance responsible for managing DR operations like failover, failback, and replication workflows.

**SSH key name**:

The name of the IBM Cloud SSH key used to enable secure, encrypted communication between the orchestrator and the managed VMs involved in DR automation.


**DR Schematics workspace connection status**:

Indicates whether the orchestrator is successfully connected to the Schematics workspace. A status like “ACTIVE” signifies that IaC automation is correctly integrated.

**DR Power Virtual Server workspace**:

The name of the Power Virtual Server workspace associated with the primary orchestrator. This workspace includes the virtual server infrastructure used for DR operations.

**Standby Power Virtual Server workspace**:

Represents the workspace linked to the standby orchestrator, located in a separate region. It provides backup infrastructure to take over during a failover.

**Standby orchestrator status**:

Displays the operational state of the standby orchestrator. A **failed** status indicates a misconfiguration or outage, requiring immediate attention.

**Orchestrator external connectivity status**:

Shows whether the orchestrator can reach all required IBM Cloud APIs and external services to perform DR operations.

 - **Active**: All required external services are reachable.
 - **Inactive**: One or more external services are not reachable.

 **Standby orchestrator status**:

 Shows whether the standby orchestrator VM is operational.
 
- **Active**: Standby orchestrator is healthy and ready.
- **Failed**: Standby orchestrator has encountered issues and may not be available for failover.

**DR Orchestrator status**:

Displays the current operational status of the primary orchestrator. A status such as “Active” indicates that the orchestrator is functioning and ready for DR activities.

**DR Schematics workspace**:

Specifies the name of the IBM Cloud Schematics workspace that contains the Infrastructure as Code (IaC) configuration used by the orchestrator to provision and manage DR resources.

**DR Location**:

Displays the location (for example, `dal10`) that hosts the DR orchestrator and resources, confirming the failover target region.

**Standby orchestrator name**: 

The name of the standby orchestrator configured to take over if the primary orchestrator fails.

**DR orchestrator deployment time**:

Displays the date and time when the primary orchestrator is deployed. This helps you to plan for any upgrade or migrate of your orchestrator if you are not in the latest level. You can review the availability of latest levels through ksysmgr commands. For more details see [Installing the KSYS fileset](https://www.ibm.com/docs/en/vmrmdr/1.9.0?topic=installing-#install_ksys__vmrmdr_ksys_install__title__1).

**Standby Orchestrator deployment time**:

Displays the date and time when the standby orchestrator was deployed.

## Service details
{: #service-det}

**Service name**:  

Indicates the user-defined name of the DR service instance that appears on the IBM Cloud console for easy identification.

**Disaster recovery location**:

Specifies the target data center (for example, `dal10`) where the DR operations, such as failover, will take place.

**Resource group**:

Displays the IBM Cloud resource group to which this DR service belongs. Resource groups help in organizing and managing access and billing across cloud resources.

**Service CRN**:

A Cloud Resource Name (CRN) uniquely identifying the DR service instance. This identifier is useful for tracking, API access, and integration with other IBM Cloud services.

**Plan name**:

Displays the subscription plan for the Power Virtual Server DR Automation service which is selected during initial deployment. The values are **DR Automation Public Plan**, **DR Automation Private Plan**.

## Global replication services pair
{: #grs-serv-pai}

The **Global Replication Services Pair** section provides an overview of the source and target sites used in DR automation. When a Power Virtual Server (PowerVS) virtual machine (VM) is managed through DR automation, the associated replication pair is automatically displayed in this section.

Each GRS pair defines a primary site (**Site 1**) and a secondary site (**Site 2**) that are configured to work together for replication and failover.

### What you can view
{: #wha-you-can-vi}

In the **Global Replication Services Pair** section, you can see the following details:

- **Site 1**: The source region where the VM is deployed.
- **Site 2**: The destination region used for backup and recovery.

These region pairs are pre-configured and automatically populated based on the region selected during VM management.
