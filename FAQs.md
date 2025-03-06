---
copyright:
  years: 2025
lastupdated: "2025-03-06"

subcollection: dr-automation

keywords: faqs

---
# FAQs
{: #faqss}

The FAQ section provides concise answers to common questions about {{site.data.keyword.DR_full}} for PowerVS, covering its features, billing model, components, deployment across regions, prerequisites, monitoring tools, security, and more. It aims to help users understand and efficiently use DR Automation for disaster recovery in IBM Power Virtual Server environments.
{:shortdesc: .shortdesc}

 ## **What is {{site.data.keyword.DR_full}} for PowerVS?**  
 
DR Automation for PowerVS is a solution for automating disaster recovery operations for IBM Power Virtual Server environments. It ensures seamless failover, failback, and data synchronization between primary and backup sites. This service is integrated with the IBM Cloud Catalog UI, enabling users to deploy and manage DR solutions efficiently.  
[Learn more about {{site.data.keyword.DR_short}}](/docs/dr-automation-powervs)

 ## **How does {{site.data.keyword.DR_full_notm}} simplify DR processes?**
 {: #how to}  

The solution minimizes manual intervention by automating DR workflows using tools like the DR Service Broker and the KSYS orchestrator. These components synchronize resources, manage failover priorities, and optimize RPOs and RTOs, ensuring high availability and business continuity.

## **What billing model does DR Automation use?**
 {: #bill}    

DR Automation is billed based on the **number of cores provisioned** for disaster recovery. Unlike traditional setups that may include storage and additional configuration costs, DR Automation for PowerVS focuses solely on compute cores. Use the IBM Cloud estimator tool to calculate costs.  


## **What is the role of the DR Orchestrator (KSYS)?**
{: #role}  

KSYS orchestrates DR operations by managing the sequence of recovery, ensuring workloads are restored in a logical order. It handles failover and failback processes across regions, optimizing resource usage during disasters.  
  
## **What is the DR Service Broker?**
{: #srd}  

This component provides a centralized interface for provisioning and managing DR resources. It ensures seamless integration with IBM Cloud services and securely updates billing metrics and usage data for each instance.  
  
## **Can DR Automation be deployed across multiple regions?**
{: #dep}  

Yes, DR Automation supports global IBM Cloud regions, allowing users to select the primary and backup sites. It ensures low-latency failovers and adheres to region-specific compliance requirements.  

## **What are the prerequisites for setting up DR Automation?**
{: #preque}  

- **IBM Cloud Account:** Create and log in to an IBM Cloud account.  
- **SSH Keys:** Configure keys for secure communication with PowerVS instances.  
- **VPC Configurations:** Define virtual private cloud settings for data isolation.  
- **Infrastructure Plan:** Review capacity needs using IBM's cost estimator.  

## **What steps are involved in provisioning {{site.data.keyword.DR_short}}?**
{: #hekp} 

   The provisioning workflow starts with the Service Broker deploying KSYS VMs in the source workspace. Data synchronization and resource replication are initiated automatically, with real-time updates visible in the UI.

## **What storage tiers are supported for {{site.data.keyword.DR_short}}?**
{: #suppt}  

   DR Automation focuses on compute resources, but if storage is required, it supports flexible configurations like Tier 0 (25 IOPS/GB) and Tier 3 (3 IOPS/GB) for different workload requirements.

##  **Does DR Automation support High Availability (HA)?**
{: #hadr}  

Yes, optional HA configurations can be enabled for orchestrators, ensuring resilience against single points of failure during disasters.  

## **What monitoring tools are available?**
{: #monitor}  

IBM Cloud Monitoring provides dashboards for tracking DR health metrics, failover progress, and potential anomalies, ensuring real-time visibility.  

## **How does DR Automation handle data isolation?**
{: #dataisol}  

- **VPC Networks:** Ensures private IP configurations.  
- **Encryption:** Uses AES-256 for data at rest and TLS for data in transit.  

## **Can users customize recovery priorities?**
{: #drcp}  

Yes, recovery configurations are customizable, allowing users to prioritize critical workloads and define VM-specific failover settings.

## **Is there a way to test DR readiness?**
{: #drread}    

The platform includes features for DR drills, where users can simulate failovers to verify recovery workflows and ensure system readiness.

## **What are the main API endpoints for {{site.data.keyword.DR_short}}?**
{: #apiendd}  

Key endpoints include provisioning APIs for deploying KSYS VMs, monitoring APIs for health metrics, and deprovisioning APIs for tearing down configurations.  

## **Does DR Automation support scaling?**
{: #scaling}  

Yes, users can scale resources dynamically based on workload demands. Additional cores can be provisioned through the IBM Cloud UI.

## **How is security ensured in {{site.data.keyword.DR_short}}?**
{: #secui}   

- **IAM Roles:** Role-based access control for resource operations.  
- **Data Encryption:** Protects sensitive recovery data in transit and at rest.  

## **What are the key components of {{site.data.keyword.DR_short}}?**
{: #compe}  

- **KSYS Orchestrator:** Manages failover/failback workflows.  
- **Service Broker:** Handles resource provisioning.  
- **Cloud Object Storage:** Supports backup data replication.  

## **How can users track billing for {{site.data.keyword.DR_short}}?**
{: #implemen}  

Billing is transparent and tied to the number of cores. Usage metrics are updated in real-time in the IBM Cloud billing dashboard.  

## **What support options are available for {{site.data.keyword.DR_short}}?**
{: #supo}  

IBM offers 24/7 technical support, comprehensive documentation, and guided assistance for setting up and managing DR Automation.  

## **What resources should be planned before implementing VMRM DR ?**
{: #implementt}   

Before implementing the VM Recovery Manager (VMRM) DR solution, ensure you have the following resources planned and ready:  

- **KSYS Node**: Identify the virtual machine running IBM AIX 7.3 with Technology Level 1 Service Pack 1 (7300-01-01) or later, capable of communication with both active and backup sites via HTTPS.

- **KSYS Cluster**: Choose a name for your cluster with the type set to IBM_PVS_DR.  
- **Active and Backup Sites**: Identify and name both sites for proper failover configuration.  
- **LPARs**: Ensure LPARs are part of the active site and not set for automatic restart.  
- **Cloud Storage**: Set up cloud storage compatible with cloud storage APIs to manage data replication between sites.  

## **What is the role of the KSYS node in DR operations for PowerVS?**
{: #roleksys}  

The KSYS node is responsible for managing disaster recovery operations across active and backup sites. It must be a virtual machine running IBM AIX 7.3 or later, capable of communicating with both sites via HTTPS. The node handles failover and ensures data replication between sites by interacting with cloud storage and VMs.  

## **What configurations are required for cloud storage in DR Automation for PowerVS?**
{: #what conf} 

Cloud storage must be configured with versions from 73D onwards to ensure that the KSYS node can interact with the cloud APIs for data replication and availability. This is critical to ensure smooth failover and recovery between the active and backup sites.  

## **When orchestrator deployment is not completed and finish button is not enabled in UI?**
{: #orch-fini-enab} 

Once the orchestrator VM is deployed and active, the cluster configuration starts automatically. Once it is completed, KSYS sends an event, and the UI enables the **Finish** button to launch the external orchestrator UI.

If there are any communication issues preventing the orchestrator VM from sending the event, the **Finish** button is not enabled, and you will not be able to enable DR for managed VM's using the External Orchestrator UI.

To know more about  [why is the **Finish** button not enabled in the UI after orchestrator deployment?](/docs/dr-automation-powervs?topic=dr-automation-powervs-troubleshooting#orch-fini-enab).

Follow the below steps to verify any communication issues:

1. Log in to the Orchestrator VM from the IBM Cloud UI or through the jump server VSI created during the VPC landing zone deployment.

2. Validate the communication using the below link:
   `curl -v` [power-dra.cloud.ibm.com](power-dra.cloud.ibm.com)
    OR
   `curl -v` [www.google.com](www.google.com).

3. Export the proxy server IP configured on Edge VSI that is created through the VPC landing zone and perform the step two to check the communication.

   > `export http_proxy="<proxy_ip:port>"`
   > `export https_proxy="<proxy_ip:port>"`

   > **Example:**
   > `export http_proxy="10.30.10.4:3128"`
   > `export https_proxy="10.30.10.4:3128"`

- If the communication issue persists you can check the status of the squid service on Edge VSI.

- To check the squid proxy status, run the following command on Edge VSI server

  `systemctl status squid`

- If the service is not running, run the following command to restart the squid service

  `systemctl restart squid`

  For more information refer to[Power Virtual Server with VPC landing zone](/docs/deployable-reference-architectures?topic=deployable-reference-architectures-deploy-arch-ibm-pvs-inf-standard).
