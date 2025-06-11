---
copyright:
  years: 2025
lastupdated: "2025-06-11"

subcollection: dr-automation

keywords: deploy the orch

---

# Deploying the orchestrator
{: #idep-the-orch}

After creating the resource, deploying the orchestrator for DR automation is essential to ensure that your Power Virtual Server environment is protected against disaster events. The orchestrator coordinates disaster recovery operations, including replication, failover, and failback of virtual machines. This screen displays high availability (HA) settings, authentication keys and resource allocation. Once deployed, the orchestrator can manage multiple virtual servers and help ensure continuous availability.
{:shortdesc: .shortdesc}

 >**Note**: 
>- The orchestrator VM is created with the default configuration of 0.5 CPU units and 4 GB memory.
>- This configuration is suitable for managing 20 PowerVS instances.
>- If you need to manage more than 20 Managed VMs, it is recommended to increase the configuration to 1 CPU unit and 6 GB of memory.

## Deploying the orchestrator for disaster recovery
{: #dep-the-orch-dis-re}

### Procedure 
{: #procedure}

To deploy the orchestrator with the necessary configurations to meet your disaster recovery requirements,
follow the steps:

1. After completing the **Create** resource step, you are redirected to the **Manage** tab to proceed with the deployment.

2. In the configure primary orchestrator section, enter the **DR Orchestrator name**.

3. Set a password in the **DR Orchestrator password** field and re-enter the password in **Confirm DR orchestrator password** section to secure access to the external orchestrator interface.
   > **Note**: This password is set for the Orchestrator VM, and you can use it to login to the Orchestrator VM UI.

4. Provide a valid **IBM Cloud API key**.
   > **Note**: Enter your API key, which is required to access various services described in [Access role requirements for Power Virtual Server DR Automation](/docs/dr-automation-powervs?topic=dr-automation-powervs-iam-manage#ser-acc-role-dr-auto). Ensure that the API key has the necessary permissions for proper functionality.

5. In the **DR location** field, select the target region for deploying the orchestrator VM.

6. Select **Schematic workspace** or **Custom VPC** to manually configure the network settings for the orchestrator deployment.

   - Select **Schematic workspace** and follow these steps:

      1. Select an appropriate workspace for the orchestrator in the **DR Schematic workspace (VPC)** field.
      2. Create a [VPC landing zone](https://cloud.ibm.com/catalog/architecture/deploy-arch-ibm-pvs-inf-2dd486c7-b317-4aaa-907b-42671485ad96-global/readme/terraform/terraform/e104e91d-d4a8-44fa-a341-eebf735d9635-global) if required, to define the Power Virtual Server workspace where the primary orchestrator is deployed.
         > **Note**: The schematic ID is available if the VPC is created by using the VPC Landing Zone for the PowerVS option from the catalog. If VPCs are created manually, you can still generate a schematic ID by using the Import option in the VPC Landing Zone for PowerVS.
   - Select **Custom VPC** and follow these steps:

      1. Select the **Transit Gateway** to establish connectivity between the VPC and the PowerVS environment.
      2. Choose the VPC from the dropdown that is attached to the **Transit gateway** in the previous step.
      3. Enter the Proxy details in `proxyIP:portno` format to enable secure communication between the Orchestrator and external IBM Cloud services, see the [FAQ](/docs/dr-automation-powervs?topic=dr-automation-powervs-faqs#vpc-vsi-enab) to find the ProxyIP of the VSI.
      
7. Select the **DR Power Virtual Server workspace** that is listed based on the selected **DR location** and **DR Schematics workspace**. Accordingly, to change the DR Power Virtual Server workspace, update the DR location and DR Schematics workspace.

8. Under **Public SSH Key**, enable the **Use a secret** radio button to use a secret from Secrets Manager. Click **Select from Secrets Manager** and select **Service Instances**, **Secret Groups**, and **Secrets**.

9. Select the SSH key from **SSH key name**.

10.  (Optional) Modify the **Advanced Settings** to configure the Storage tier and Machine type based on the **Deploy Orchestrator with HA** selection.

11. In **Configure standby orchestrator (for HA)**, enter the **Standby orchestrator name** and select a **Standby Power Virtual Server workspace** to define the Power Virtual Server workspace in which the standby orchestrator is deployed, when HA is enabled during provision. These settings enable the orchestrator to provide continuous recovery capabilities if the primary site fails.

12. After verifying all settings, click **Deploy orchestrator** to start the deployment process, which creates the orchestrator VMs.

13. Once the orchestrator VM is deployed, manage the service through the **External orchestrator interface** and configure additional virtual server instances for disaster recovery.

  >**Note**: The orchestrator interface (UI) is launched at https://`<Orchestrator IP>`:3000/login. The `<Orchestrator IP>` is the system on which the orchestrator UI is installed and it is loaded automatically.

14. Enable the **External standby orchestrator interface** to allow the orchestrator to manage failover operations by recognizing a standby orchestrator for redundancy and resilience, following the steps:

      a. Complete the [External orchestrator interface setup](/docs/dr-automation-powervs?topic=dr-automation-powervs-manage-exter).  
      b. Hover over the **External standby orchestrator interface** button to view the standby orchestrator IP, for example, `IP:xx.x.x.xxx`.  
      c. Use the standby orchestrator IP and add it in the [**Add Node**](/docs/dr-automation-powervs?topic=dr-automation-powervs-nav-pan#ksys-set-tab-detai) section.  
      d. Click the **External standby orchestrator interface** button to enable the interface.  
      e. Click the **Refresh** icon to update the status, enabling the **External standby orchestrator interface button** for use.
15. If any error occurs during deployment, follow on-screen prompts to troubleshoot and retry the deployment.

By following this process, you can ensure that your orchestrator is fully equipped to manage disaster recovery operations for your virtual servers.

## Power Edge Router and non Power Edge Router

Power Virtual Server DR Automation supports both Power Edge Router(PER) and non Power Edge Router(PER) workspaces.
To use a non PER enabled workspace, complete the following manual steps before using them:

1. Create a Cloud connection by attaching all the available subnets that are used for communication.
2. Verify that the Cloud connection status changes to Active.
3. Attach the Cloud connection to the Transit gateway.
4. Select the Transit gateway **->** Add connection **->** Select Direct Link and select the newly created direct link **->** click Add.

 The **Orchestrator Details** and **Service Details** sections provide comprehensive technical insights that help administrators and cloud engineers monitor and manage disaster recovery automation for their infrastructure.
 
## Orchestrator details
{: #orc-det}
 The **Orchestrator Details** and **Service Details** sections provide comprehensive technical insights that help administrators and cloud engineers monitor and manage disaster recovery automation for their infrastructure.

**DR Orchestrator name**:  
The unique identifier for the primary orchestrator instance responsible for managing DR operations like failover, failback, and replication workflows.

**DR Orchestrator status**:  
Displays the current operational status of the primary orchestrator. A status such as “Active” indicates that the orchestrator is functioning and ready for DR activities.

**SSH key name**:  
The name of the IBM Cloud SSH key used to enable secure, encrypted communication between the orchestrator and the managed VMs involved in DR automation.

**DR Schematics workspace**:  
Specifies the name of the IBM Cloud Schematics workspace that contains the Infrastructure as Code (IaC) configuration used by the orchestrator to provision and manage DR resources.

**DR Schematics workspace connection status**:  
Indicates whether the orchestrator is successfully connected to the Schematics workspace. A status like “ACTIVE” signifies that IaC automation is correctly integrated.

**DR Location**:  
Displays the location (for example, `dal10`) that hosts the DR orchestrator and resources, confirming the failover target region.

**DR Power Virtual Server workspace**:  
The name of the Power Virtual Server workspace associated with the primary orchestrator. This workspace includes the virtual server infrastructure used for DR operations.

**Standby Power Virtual Server workspace**:  
Represents the workspace linked to the standby orchestrator, located in a separate region. It provides backup infrastructure to take over during a failover.

**Standby orchestrator name**:  
The name of the standby orchestrator configured to take over if the primary orchestrator fails.

**Standby orchestrator status**:  
Displays the operational state of the standby orchestrator. A “failed” status indicates a misconfiguration or outage, requiring immediate attention.

**Orchestrator external connectivity status**:  
Indicates the network connectivity of the orchestrator with external components and services. A status of “Active” confirms that all required external connections are functional.

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
