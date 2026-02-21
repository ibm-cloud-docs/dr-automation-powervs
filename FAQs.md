---
copyright:
  years: 2025
lastupdated: "2026-02-21"

subcollection: dr-automation-powervs

keywords: faqs, help, FAQ, answers

---
# FAQs
{: #faqs}

The FAQ section provides concise answers to common questions about {{site.data.keyword.DR_full}} for PowerVS, covering its features, billing model, components, deployment across regions, prerequisites, monitoring tools, security and more. It aims to help users understand and efficiently use DR Automation for disaster recovery in IBM Power Virtual Server environments.
{:shortdesc: .shortdesc}

## {{site.data.keyword.DR_full_notm}} faq's

### **What is {{site.data.keyword.DR_full}} ?**  
 {: #how-to-power-vs}

{{site.data.keyword.DR_full_notm}} is an IBM Cloud service that helps you automate high availability (HA) and disaster recovery (DR) for workloads running on IBM Power Virtual Server (PowerVS).
The service simplifies how you protect PowerVS workloads by automating:

- Failover and recovery workflows
- Monitoring of protected environments
- Coordination between primary and secondary systems

It reduces manual intervention and helps improve application availability and resilience.
[Learn more about {{site.data.keyword.DR_short}}](/docs/dr-automation-powervs)

### What are the different plans available for {{site.data.keyword.DR_full_notm}}?

{{site.data.keyword.DR_full_notm}} is offered as a single service with multiple plans, each designed for a specific deployment model. The available plans are:

- **PowerVS Public DR Automation**

This plan is designed for Power Virtual Server instances running in IBM Cloud public regions.
It enables disaster recovery automation for workloads hosted and managed within IBM Cloud PowerVS data centers.

Use this plan when your PowerVS instances are deployed in IBM Cloud public locations.

- **PowerVS Private DR Automation**

This plan is intended for private or client-owned PowerVS environments.
It supports disaster recovery automation where PowerVS infrastructure is deployed in a dedicated or private setup, outside of IBM Cloud public regions.

Use this plan when your PowerVS environment is deployed in a private or client location.

- **PowerHA AIX for PowerVS**

This plan provides PowerHA enablement for AIX workloads running on PowerVS.
It is focused on high availability (HA) rather than disaster recovery and is available only in locations that support PowerHA for AIX on PowerVS.

Use this plan when you require high availability for AIX workloads on PowerVS.



### **How does {{site.data.keyword.DR_full_notm}} processes?**
 {: #how-to}  

The solution reduces manual effort by automating high availability (HA) and disaster recovery (DR) workflows for PowerVS environments. It helps coordinate resources, manage failover operations, and maintain recovery objectives, enabling improved application availability and business continuity with minimal manual intervention.

### **What billing model does {{site.data.keyword.DR_full_notm}} use?**
 {: #bill}

Power Virtual Server HA and DR Automation is billed based on the **number of cores provisioned** for disaster recovery per hour. Unlike traditional setups that can include storage and more configuration costs. Use the IBM Cloud estimator tool to calculate costs.  


### **Can {{site.data.keyword.DR_full_notm}} be deployed across multiple regions?**
{: #dep}

Yes, {{site.data.keyword.DR_full_notm}} can be deployed across multiple supported IBM Cloud regions. You can select supported regions as primary and secondary sites based on your availability and recovery requirements.

The service is designed to operate across regions while respecting region-specific capabilities and compliance requirements. Actual latency and recovery behavior depend on the selected regions and network configuration.


### **What storage tiers are supported for {{site.data.keyword.DR_short}}?**
{: #suppt}  

   {{site.data.keyword.DR_full_notm}} focuses on compute resources, but if storage is required, it supports flexible configurations like Tier 1 (10 IOPS/GB) and Tier 3 (3 IOPS/GB) for different workload requirements.

   > **Note**:For PowerHA AIX for PowerVS, storage is managed as part of the existing PowerVS environment.

### **Does {{site.data.keyword.DR_full_notm}} High Availability (HA)?**

Yes. High availability is supported through the PowerHA AIX for PowerVS plan, which provides native HA capabilities for AIX workloads.

### **What monitoring tools are available?**
{: #monitor}  

IBM Cloud Monitoring provides dashboards for tracking DR health metrics, failover progress and potential anomalies, can ensure real-time visibility.  

### **How does {{site.data.keyword.DR_full_notm}} handle data isolation?**
{: #dataisol}  

- **VPC Networks:** Can ensure private IP configurations.  
- **Encryption:** Uses AES-256 for data at rest and TLS for data in transit.  

### **Can users customize recovery priorities?**
{: #drcp}  

Yes, recovery configurations are customizable, allowing users to prioritize critical workloads and define VM-specific failover settings.

### **How security can be ensured in {{site.data.keyword.DR_short}}?**
{: #secui}

- **IAM Roles:** Role-based access control for resource operations.  
- **Data Encryption:** Protects sensitive recovery data in transit and at rest.  

### **What are the key components of {{site.data.keyword.DR_short}}?**
{: #compe}  

- **KSYS Orchestrator:** Manages failover/failback workflows.  
- **Service Broker:** Handles resource provisioning.  
- **Cloud Object Storage:** IBM Cloud services like Cloud Object Storage, CloudantDB, BSS, Activity Tracker, Cloud logs, Sendgrid/ACS.
- **PowerHA SystemMirror (for PowerHA plans)**: Provides native high availability capabilities for AIX workloads running on PowerVS.
- **PowerHA Agent (for PowerHA plans)**: Installs and manages PowerHA filesets on selected PowerVS instances and reports status to the service.

### **How can users track billing for {{site.data.keyword.DR_short}}?**
{: #implemen}  

Billing is transparent and tied to the number of cores. Usage metrics are updated in real time in the IBM Cloud billing dashboard.  

### **What support options are available for {{site.data.keyword.DR_short}}?**
{: #supo}  

IBM offers 24/7 technical support, comprehensive documentation and guided assistance for setting up and managing DR Automation.  

## Power Virtual Server DR Automation faq:
{: #power-vs-dr-auto-faq} 

### **What is the role of the DR Orchestrator (KSYS)?**
{: #role}  

KSYS as orchestrator (VM) DR operations by managing the sequence of recovery, can ensure that workloads are restored in a logical order. It handles failover and failback processes across regions, optimizing resource usage during disasters.  

### **What are the prerequisites for setting up DR Automation?**
{: #preque}  

- **IBM Cloud Account:** Create and log in to an IBM Cloud account.  
- **SSH Keys:** Configure keys for secure communication with PowerVS instances.  
- **VPC Configurations:** Define virtual private cloud settings for data isolation.  
- **Infrastructure Plan:** Review capacity needs that use IBM's cost estimator.
For more details, refer to [Before you begin](/docs/dr-automation-powervs?topic=dr-automation-powervs-getting-started).

### **What is the DR Service Broker?**
{: #srd}  

This component provides a centralized interface for provisioning and managing DR resources. It can ensure seamless integration with IBM Cloud services and securely updates billing metrics and usage data for each instance.

### **Is there a way to test DR readiness?**
{: #drread}

The platform includes features for DR drills, where users can simulate failovers to verify recovery workflows and can ensure system readiness.

### **Does DR Automation support scaling?**
{: #scaling}  

Yes, users can scale resources dynamically based on workload demands. Additional cores can be provisioned through the IBM Cloud UI.

### **What are the key components of {{site.data.keyword.DR_short}}?**
{: #compe}  

- **KSYS Orchestrator:** Manages failover/failback workflows.  
- **Service Broker:** Handles resource provisioning.  
- **Cloud Object Storage:** IBM Cloud services like Cloud Object Storage, CloudantDB, BSS, Activity Tracker, Cloud logs, Sendgrid/ACS.
- **PowerHA SystemMirror (for PowerHA plans)**: Provides native high availability capabilities for AIX workloads running on PowerVS.
- **PowerHA Agent (for PowerHA plans)**: Installs and manages PowerHA filesets on selected PowerVS instances and reports status to the service.

### **What resources should be planned before implementing DR Automation?**
{: #implementt}   

Before implementing the DR Automation solution, can ensure that you have the following resources planned and ready:  

- **KSYS Node**: Identify the virtual machine runs IBM AIX 7.3 with Technology Level 1 Service Pack 1 (7300-01-01) or later, capable of communication with both active and backup sites through HTTPS.

- **KSYS Cluster**: Choose a name for your cluster with the type set to IBM_PVS_DR.  
- **Active and Backup Sites**: Identify and name both sites for proper failover configuration.  
- **LPARs**: Can ensure LPARs are part of the active site and not set for automatic restart.  
- **Cloud Storage**: Set up cloud storage compatible with cloud storage APIs to manage data replication between sites.

### **What are the main API endpoints for PowerVS DR Automation?**
{: #apiendd}  

Key endpoints include provisioning APIs for deploying KSYS VMs, monitoring APIs for health metrics, and deprovisioning APIs for tearing down configurations. Some APIs and workflows apply only to DR Automation plans.


### **What is the role of the KSYS node in DR operations for PowerVS?**
{: #roleksys}  

The KSYS node is responsible for managing disaster recovery operations across active and backup sites. It must be a virtual machine runs IBM AIX 7.3 or later, capable of communicating with both sites through HTTPS. The node handles failover and can ensure data replication between sites by interacting with cloud storage and VMs.

### **What configurations are required for cloud storage in DR Automation for PowerVS?**
{: #what-conf} 

Cloud storage must be configured with versions from AIX 7.3 TL2 onwards to can ensure that the KSYS node can interact with the cloud APIs for data replication and availability. This is critical to can ensure smooth failover and recovery between the active and backup sites. 


### **When orchestrator deployment is not completed and the finish button is not enabled in UI?**
{: #orch-fini-enab} 

Once the orchestrator VM is deployed and active, the cluster configuration starts automatically. Once it is completed, KSYS sends an event, and the UI enables the **Finish** button to launch the external orchestrator UI.

If there are any communication issues preventing the orchestrator VM from sending the event, the **Finish** button is not enabled, and you will not be able to enable DR for managed VM's using the External Orchestrator UI.

To know more about [why is the **Finish** button not enabled in the UI after orchestrator deployment](/docs/dr-automation-powervs?topic=dr-automation-powervs-troubleshooting#orch-fini-enab).



### How to get ProxyIP details which is configured for Virtual Server Instance for VPC?
{: #vpc-vsi-enab}

The proxy IP is the private IP address assigned to a Virtual Server Instance (VSI) in a Virtual Private Cloud (VPC). It enables secure communication with other resources. Follow these steps to retrieve the proxy IP from the IBM Cloud console:

1. Log in to the [IBM Cloud console](https://cloud.ibm.com).
2. Click **Infrastructure** > **Virtual server instances**.
3. Select the VSI from the list (for example, `test-vsi-test`).
4. Click the VSI name to open its details page.
5. Select the **Networking** tab.
6. Locate the **Reserved IP** in the network attachments section, by default squid uses this reserved IP for the configuration.
7. If the VSI has multiple IPs and you configured `squid.conf` with different IP, that is in `/etc/squid/squid.conf` with the following entry:

> `http_port <IP>:3128`

The IP is used as a proxy IP in squid configuration.

To enable communication to external services, export the following variables on your orchestrator node:

>`http_proxy="<ProxyIP>:3128"`
>
>`https_proxy="<ProxyIP>:3128"`
>
> **Note**: Exporting these variables is automatic with the DR Deployment, you can validate the configuration using these variables.
> **Note**: The updated proxy details are not reflected in the DR Automation UI. The UI continues to display only the initially configured proxy IP.

### Why is IBM Data Center not displayed as the location type during provisioning?
{: #location-type}

The location type displayed during provisioning depends on the selected plan. This behavior is expected and reflects the infrastructure that is associated with each deployment model.

**Public plan**: Displays **IBM Data Center** as the location type, as the infrastructure is hosted and managed in IBM Cloud regions.

**Private plan**: Displays **Client Location** as the location type, indicating that the infrastructure is physically deployed at the client site and managed remotely by IBM.

This mapping is intentional and helps distinguish between public and private (on-premises, Private Pod environments) cloud deployments.

### **What should I do if I accidentally delete a KSYS Cluster?**
{: #delete-ksys}

If a KSYS Cluster is deleted, you must re-create the cluster in the external orchestror GUI:

#### Procedure
{: #pro-proxy}

1. Log in to the GUI.  
2. Go to the **Add KSYS Subsystem** page.  
3. Click **Add KSYS** and provide the host details (Username and Password).  
4. Select the correct **KSYS Deployment Type**:  
   - **IBM_PVS_DR** for standard DR  
   - **IBM_PVS_PRIVATE_DR** for private PowerVS cluster environments  
5. Re-enter the **Cluster Details**.  
6. (Optional) Enable **Add Proxy** if communication requires a proxy.  
7. Save the configuration to restore orchestrator functionality.  

### **How do I create a new KSYS Cluster in external orchestrator?**
{: #create-ksys-cluster}

When you log in for the first time in external orchestror, or if no cluster exists, you are redirected to the **Add KSYS Subsystem** page. From there you can perform the following actions:  
- Click **Add KSYS**  
- Enter host details (Username, Password)  
- Select **IBM_PVS_DR** or **IBM_PVS_PRIVATE_DR**  
- Provide cluster details  
- (Optional) enable proxy support  
- Click **Save & Next**  

### **When should I choose IBM_PVS_DR vs IBM_PVS_PRIVATE_DR?**
{: #ksys-types}

- **IBM_PVS_DR** → For standard DR deployments across IBM Cloud regions.  
- **IBM_PVS_PRIVATE_DR** → For private PowerVS cluster environments, such as on-premises or private pods.

### **How do I update the Proxy IP in the Orchestrator?**
{: #proxy-ip}

You can update the proxy IP in the orchestrator depending on whether the KSYS cluster has already been created. To update the Proxy IP, follow the steps below.

#### **Step 1: Cluster already created**
{: #proxy-existing}

1. Verify the cluster status by running the following command:

   ```ksysmgr query ksyscluster```

2. If the cluster exists, update the proxy IP using the following command:

   ```ksysmgr modify ksyscluster <ksysclustername> proxy=ipaddress:portnumber```

#### **Step 2: Cluster not yet created**
{: #proxy-new}

If the KSYS cluster is not yet created, you can update the proxy IP directly in the configuration file.

1. Navigate to the `/etc` directory and back up the existing configuration file:  

   ```#cp /etc/drautomation.json /etc/drautomation.json.bkp```

2. Open the `/etc/drautomation.json` file in a text editor.  
3. Update the proxy IP and port details as required.
4. Save the file.  
5. To delete stale entries if exist, run the following command:
   > ```rm -f /var/ksys/config/ksys_configured.txt```

When the system reboots, it automatically attempts to recreate the cluster with the updated proxy configuration.

## **How do I update the API Key in my DR Automation deployment?**
{: #update-api-key}

You can update the API Key for your deployment using the DR Automation UI and the KSYS Orchestrator. Ensure that the same key is used in both places to maintain proper synchronization.

### **Step 1: Update the API Key in DR Automation UI**
{: #update-api-ui}

1. Navigate to the **Summary** page in the DR Automation UI.  
2. Click the **Update API Key** button.  
3. The system updates the API key for your deployment automatically.

#### **Step 2: Update the API Key in Orchestrator**
{: #update-api-orch}

After updating the API key in the UI, update it in the orchestrator to keep both in sync:

To update the API key in orchestrator ,run the following command:

   ```ksysmgr modify ksyscluster <ksysclustername> apikey=<apikey>```
> **Note:** Use the same API key in both the deployment and orchestrator to ensure proper synchronization.

## PowerHA faq
{: #powerha-faq}

### **What are the prerequisites for setting up PowerHA AIX for PowerVS?**
{: #preque-powerha}

Before you deploy PowerHA AIX for PowerVS, ensure that the following requirements are met:

- **IBM Cloud account** - You must have an active IBM Cloud account. If required, sign up at https://cloud.ibm.com/registration.
- **IAM access** - Configure the required Identity and Access Management (IAM) roles and permissions for PowerHA AIX for PowerVS.
- **PowerVS environment** - A supported Power Virtual Server workspace with AIX virtual machines must already be available in the selected location.
- **Infrastructure planning** - Plan your high availability topology based on your business requirements and supported PowerHA configurations.
- **API key** - An IBM Cloud API key is required for service provisioning and orchestration operations.

### **What are the main API endpoints for PowerHA AIX for PowerVS?**
{: #apiendd}  

Key endpoints include provisioning APIs for VMs, monitoring APIs for health metrics, and deprovisioning APIs for tearing down configurations. Some APIs and workflows apply only to HA Automation plans.

### **What resources should be planned before implementing PowerHA AIX for PowerVS?**
{: #implementt-powerha}

Before implementing PowerHA AIX for PowerVS, ensure that you have the following resources planned and ready:

- **PowerVS AIX virtual machines**: Existing AIX virtual machines on PowerVS that will participate in the PowerHA cluster.
- **PowerHA cluster nodes**: Identify the PowerVS instances that will form the PowerHA cluster.
- **Network connectivity**: Reliable network connectivity between PowerHA nodes to support cluster communication and failover.
- **PowerHA software availability**: PowerHA SystemMirror filesets must be available for installation on each PowerHA node using the PowerHA agent.
- **Cluster configuration planning**: Plan resource groups, application dependencies, and failover behavior according to your high availability requirements.

### What APIs are available for this service?
{: #api-powerha}

The service provides the following APIs:

- **Provision API** – Creates or deletes a service instance.  
- **PHA Workspace Region API** – Retrieves available workspaces for a specified region.  
- **PVM Instances API** – Lists PowerVM instances within a selected workspace.  
- **API Key API** – Adds or retrieves the API key used for authentication.  
- **Cluster Node API** – Adds, updates, retrieves, or deletes cluster node details.  
- **PHA Deployment API** – Configures and retrieves deployment details.  
- **Deployment Update API** – Updates an existing deployment configuration and tracks status.  
- **Supported Locations API** – Lists all supported DR locations.  
- **Events API** – Retrieves lifecycle events for a service instance.  
- **Last Operation API** – Displays the status of the most recent operation performed on the service instance.  

### How do I provision or deprovision a service instance using the API?
{: #api-provision-powerha}

To provision a service instance, use the **Provision API (PUT)** and provide the required parameters, including the `crn`, `plan_id`, `service_id`, and context details such as the service name, resource group, and target.

After successful provisioning, the API response includes a `dashboard_url` that you can use to access the service instance.

To deprovision a service instance, use the **DELETE** operation with the corresponding `plan_id` and `service_id`. The response confirms that the deprovisioning process has been initiated.
