---
copyright:
  years: 2025
lastupdated: "2025-04-17"

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
following the steps:

1. After completing the **Create** resource step, you are redirected to the **Manage** tab to proceed with the deployment.

2. In the configure primary orchestrator section, enter the **DR Orchestrator name**.

3. Set a password in the **DR Orchestrator password** field and re-enter the password in **Confirm DR orchestrator password** to secure access to the external orchestrator interface.
   > **Note**: This password is set for the Orchestrator VM and you can use it to login to the Orchestrator VM UI.

4. Provide the valid **IBM Cloud API key**.
   > **Note**: Enter your API key, which is required to access various services described in [Access role requirements for Power Virtual Server DR Automation](/docs/dr-automation-powervs?topic=dr-automation-powervs-iam-manage#ser-acc-role-dr-auto). Ensure that the API key has the necessary permissions for proper functionality.

5. In the **DR location** field, select the target region for deploying the orchestrator VM.

6. In the **DR Schematic workspace (VPC)** field, select an appropriate workspace for the orchestrator. If required, create a [VPC landing zone](https://cloud.ibm.com/catalog/architecture/deploy-arch-ibm-pvs-inf-2dd486c7-b317-4aaa-907b-42671485ad96-global/readme/terraform/terraform/e104e91d-d4a8-44fa-a341-eebf735d9635-global) to define the Power Virtual Server workspace where the primary orchestrator will be deployed.
   > **Note**: The schematic ID is available if the VPC is created by using the VPC Landing Zone for the PowerVS option from the catalog. If VPCs are created manually, you can still generate a schematic ID by using the Import option in the VPC Landing Zone for PowerVS.

7. Select the **DR Power Virtual Server workspace** that is listed based on the selected **DR location** and **DR Schematics workspace**. Accordingly, to change the DR Power Virtual Server workspace, update the DR location and DR Schematics workspace .

8. Under **Public SSH Key**, enable **Use a secret** radio button to use secret form Secrets Manager. Click **Select from Secrets Manager** and select **Service Instances**, **Secret Groups** and **Secrets**.

9. Select ssh key from **SSH key name**.

10. Expand the **Advanced configuration** section to adjust additional settings for storage tiers and machine types, if applicable.

11. In **Configure standby orchestrator (for HA)** enter the **Standby orchestrator name** and select a **Standby Power Virtual Server workspace** to define the Power Virtual Sever workspace in which the standby orchestrator is deployed, when HA is enabled during provision. These settings enable the orchestrator to provide continuous recovery capabilities if the primary site fails.

12. After verifying all settings, click **Deploy orchestrator** to start the deployment process, which creates the orchestrator VMs.

13. Once the orchestrator VM is deployed, manage the service through the **External orchestrator interface** and configure additional virtual server instances for disaster recovery.

  >**Note**: The orchestrator interface (UI) is launched at https://`<Orchestrator IP>`:3000/login. The `<Orchestrator IP>` is the system on which the orchestrator UI is installed and it is loaded automatically.

14. Enable the **External standby orchestrator interface** to allow the orchestrator to manage failover operations by recognizing a standby orchestrator for redundancy and resilience.

      a. Complete the [External orchestrator interface setup](/docs/dr-automation-powervs?topic=dr-automation-powervs-manage-exter).  
      b. Hover over the **External standby orchestrator interface** button to view the standby orchestrator IP, for example, `IP:xx.x.x.xxx`.  
      c. Use the standby orchestrator IP and add it in the [**Add Node**](/docs/dr-automation-powervs?topic=dr-automation-powervs-nav-pan#ksys-set-tab-detai) section.  
      d. Click the **External standby orchestrator interface** button to enable the interface.  
      e. Click the **Refresh** icon to update the status, enabling the **External standby orchestrator interface button** for use.

15. If any error occurs during deployment, follow on-screen prompts to troubleshoot and retry the deployment.

By following this process, you can ensure that your orchestrator is fully equipped to manage disaster recovery operations for your virtual servers. The **Orchestrator Details** and **Service Details** sections provide comprehensive technical insights that help administrators and cloud engineers monitor and manage disaster recovery automation for their infrastructure.

## Orchestrator details
{: #orc-det}

**Orchestrator instance identifier:**
The unique identifier for the orchestrator instance is responsible for managing failover, failback and replication processes between the primary and DR sites.

**Orchestrator health status:**
Displays the current health and state of the orchestrator, such as "Running." The orchestrator must be operational for DR functions to be ready.

**IBM Cloud SSH key:**
Refers to the secure IBM Cloud SSH key used for authenticated and encrypted communication between the orchestrator and the managed VMs involved in DR.

**Linked SSH Key for remote access:**
Indicates the SSH key that is linked to the orchestrator for remote access to VMs. Proper configuration is crucial for secure VM operations.

**Infrastructure as Code (IaC) Environment:**
The IaC environment automates the provisioning of DR resources, using Terraform templates to define workflows for automation.

**Schematics workspace connection:**
Shows whether the orchestrator is successfully connected to the Schematics workspace. A “Running” status indicates successful infrastructure automation.

## Service details
{: #service-det}

**Disaster recovery service configuration:**
Identifies the DR service that is configured in IBM Cloud for the orchestrator, linking it to the correct DR environment.

**Data center location:**
Specifies the region or data center, such as "Dallas 12," where the DR resources are hosted and where failover will occur.

**Resource group:**
Displays the IBM Cloud resource group managing the DR resources, allowing for resource-level permissions and management.

**Globally unique identifier:**
A globally unique identifier for the DR service within IBM Cloud, enabling resource tracking and auditing across cloud environments by using APIs.
