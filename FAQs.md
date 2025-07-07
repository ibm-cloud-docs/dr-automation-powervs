---
copyright:
  years: 2025
lastupdated: "2025-07-07"

subcollection: dr-automation

keywords: faqs

---
# FAQs
{: #faqs}

The FAQ section provides concise answers to common questions about {{site.data.keyword.DR_full}} for PowerVS, covering its features, billing model, components, deployment across regions, prerequisites, monitoring tools, security and more. It aims to help users understand and efficiently use DR Automation for disaster recovery in IBM Power Virtual Server environments.
{:shortdesc: .shortdesc}

 ## **What is {{site.data.keyword.DR_full}} for PowerVS?**  
 
DR Automation for PowerVS is a solution for automating disaster recovery operations for IBM Power Virtual Server environments. It can ensure seamless failover, failback and data synchronization between primary and backup sites. This service is integrated with the IBM Cloud catalog UI, enabling users to deploy and manage DR solutions efficiently.  
[Learn more about {{site.data.keyword.DR_short}}](/docs/dr-automation-powervs)

 ## **How does {{site.data.keyword.DR_full_notm}} simplify DR processes?**
 {: #how to}  

The solution minimizes manual intervention by automating DR workflows by using tools like the DR Service Broker and the KSYS orchestrator. These components synchronize resources, manage failover priorities and optimize RPOs and RTOs, can ensure high availability and business continuity.

## **What billing model does DR Automation use?**
 {: #bill}    

DR Automation is billed based on the **number of cores provisioned** for disaster recovery per hour. Unlike traditional setups that can include storage and more configuration costs, DR Automation for PowerVS focuses solely on compute cores. Use the IBM Cloud estimator tool to calculate costs.  


## **What is the role of the DR Orchestrator (KSYS)?**
{: #role}  

KSYS as orchestrator (VM) DR operations by managing the sequence of recovery, can ensure that workloads are restored in a logical order. It handles failover and failback processes across regions, optimizing resource usage during disasters.  
  
## **What is the DR Service Broker?**
{: #srd}  

This component provides a centralized interface for provisioning and managing DR resources. It can ensure seamless integration with IBM Cloud services and securely updates billing metrics and usage data for each instance.  
  
## **Can DR Automation be deployed across multiple regions?**
{: #dep}  

Yes, DR Automation supports global IBM Cloud regions, allowing users to select the primary and backup sites. It can ensure low-latency failovers and adheres to region-specific compliance requirements.  

## **What are the prerequisites for setting up DR Automation?**
{: #preque}  

- **IBM Cloud Account:** Create and log in to an IBM Cloud account.  
- **SSH Keys:** Configure keys for secure communication with PowerVS instances.  
- **VPC Configurations:** Define virtual private cloud settings for data isolation.  
- **Infrastructure Plan:** Review capacity needs that use IBM's cost estimator.
For more details, refer to [Before you begin](/docs/dr-automation-powervs?topic=dr-automation-powervs-getting-started).

## **What steps are involved in provisioning {{site.data.keyword.DR_short}}?**
{: #hekp}

   The provisioning workflow starts with the Service Broker deploying KSYS VMs in the source workspace. Data synchronization and resource replication are initiated automatically, with real-time updates visible in the UI.

## **What storage tiers are supported for {{site.data.keyword.DR_short}}?**
{: #suppt}  

   DR Automation focuses on compute resources, but if storage is required, it supports flexible configurations like Tier 1 (10 IOPS/GB) and Tier 3 (3 IOPS/GB) for different workload requirements.

##  **Does DR Automation support High Availability (HA)?**
{: #hadr}  

Yes, optional HA configurations can be enabled for orchestrators, can ensure resilience against single points of failure during disasters.  

## **What monitoring tools are available?**
{: #monitor}  

IBM Cloud Monitoring provides dashboards for tracking DR health metrics, failover progress and potential anomalies, can ensure real-time visibility.  

## **How does DR Automation handle data isolation?**
{: #dataisol}  

- **VPC Networks:** Can ensure private IP configurations.  
- **Encryption:** Uses AES-256 for data at rest and TLS for data in transit.  

## **Can users customize recovery priorities?**
{: #drcp}  

Yes, recovery configurations are customizable, allowing users to prioritize critical workloads and define VM-specific failover settings.

## **Is there a way to test DR readiness?**
{: #drread}    

The platform includes features for DR drills, where users can simulate failovers to verify recovery workflows and can ensure system readiness.

## **What are the main API endpoints for {{site.data.keyword.DR_short}}?**
{: #apiendd}  

Key endpoints include provisioning APIs for deploying KSYS VMs, monitoring APIs for health metrics, and deprovisioning APIs for tearing down configurations.  

## **Does DR Automation support scaling?**
{: #scaling}  

Yes, users can scale resources dynamically based on workload demands. Additional cores can be provisioned through the IBM Cloud UI.

## **How is security can ensure in {{site.data.keyword.DR_short}}?**
{: #secui}   

- **IAM Roles:** Role-based access control for resource operations.  
- **Data Encryption:** Protects sensitive recovery data in transit and at rest.  

## **What are the key components of {{site.data.keyword.DR_short}}?**
{: #compe}  

- **KSYS Orchestrator:** Manages failover/failback workflows.  
- **Service Broker:** Handles resource provisioning.  
- **Cloud Object Storage:** IBM Cloud services like Cloud Object Storage, CloudantDB, BSS, Activity Tracker, Cloud logs, Sendgrid/ACS.  

## **How can users track billing for {{site.data.keyword.DR_short}}?**
{: #implemen}  

Billing is transparent and tied to the number of cores. Usage metrics are updated in real time in the IBM Cloud billing dashboard.  

## **What support options are available for {{site.data.keyword.DR_short}}?**
{: #supo}  

IBM offers 24/7 technical support, comprehensive documentation and guided assistance for setting up and managing DR Automation.  

## **What resources should be planned before implementing VMRM DR?**
{: #implementt}   

Before implementing the VM Recovery Manager (VMRM) DR solution, can ensure that you have the following resources planned and ready:  

- **KSYS Node**: Identify the virtual machine runs IBM AIX 7.3 with Technology Level 1 Service Pack 1 (7300-01-01) or later, capable of communication with both active and backup sites through HTTPS.

- **KSYS Cluster**: Choose a name for your cluster with the type set to IBM_PVS_DR.  
- **Active and Backup Sites**: Identify and name both sites for proper failover configuration.  
- **LPARs**: Can ensure LPARs are part of the active site and not set for automatic restart.  
- **Cloud Storage**: Set up cloud storage compatible with cloud storage APIs to manage data replication between sites.  

## **What is the role of the KSYS node in DR operations for PowerVS?**
{: #roleksys}  

The KSYS node is responsible for managing disaster recovery operations across active and backup sites. It must be a virtual machine runs IBM AIX 7.3 or later, capable of communicating with both sites through HTTPS. The node handles failover and can ensure data replication between sites by interacting with cloud storage and VMs.  

## **What configurations are required for cloud storage in DR Automation for PowerVS?**
{: #what conf} 

Cloud storage must be configured with versions from AIX 7.3 TL2 onwards to can ensure that the KSYS node can interact with the cloud APIs for data replication and availability. This is critical to can ensure smooth failover and recovery between the active and backup sites.  

## **When orchestrator deployment is not completed and the finish button is not enabled in UI?**
{: #orch-fini-enab} 

Once the orchestrator VM is deployed and active, the cluster configuration starts automatically. Once it is completed, KSYS sends an event, and the UI enables the **Finish** button to launch the external orchestrator UI.

If there are any communication issues preventing the orchestrator VM from sending the event, the **Finish** button is not enabled, and you will not be able to enable DR for managed VM's using the External Orchestrator UI.

To know more about [why is the **Finish** button not enabled in the UI after orchestrator deployment](/docs/dr-automation-powervs?topic=dr-automation-powervs-troubleshooting#orch-fini-enab).



## How to get ProxyIP details which is configured for Virtual Server Instance for VPC?
{: #vpc-vsi-enab}

The proxy IP is the private IP address assigned to a Virtual Server Instance (VSI) in a Virtual Private Cloud (VPC). It enables secure communication with other resources. Follow these steps to retrieve the proxy IP from the IBM Cloud console:

1. Log in to the [IBM Cloud console](https://cloud.ibm.com).
2. Click **Infrastructure** > **Virtual server instances**.
3. Select the VSI from the list (for example, `test-vsi-test`).
4. Click the VSI name to open its details page.
5. Select the **Networking** tab.
6. Locate the **Reserved IP** in the network attachments section, by default squid uses this reserved IP for the configuration.
