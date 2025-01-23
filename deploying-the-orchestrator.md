---
copyright:
  years: 2025
lastupdated: "2025-01-23"

subcollection: dr-automation

keywords: deploy the orch

---

# Deploying the orchestrator
{: #idep-the-orch}

After creating the resource deploying the orchestrator for DR Automation is critical in ensuring your Power Virtual Server environment is protected against disaster events. The orchestrator coordinates disaster recovery operations, including replication, failover, and failback of virtual machines. On this screen, high availability (HA) settings, authentication keys, and resource allocation. Once deployed, the orchestrator can manage multiple virtual servers and ensure continuous availability.
{:shortdesc: .shortdesc}

## Procedure 
{: #procedure}

Following the procedure below, you can deploy the orchestrator with the necessary configurations to meet your disaster recovery requirements.

## Deploying the orchestrator for disaster recovery
{: #dep-the-orch-dis-re}

Following the procedure below, you can deploy the orchestrator with the necessary configurations to meet your disaster recovery requirements.

1. After completing the **Create** resource step, you are redirected to **Manage** tab to proceed with the deployment.

2. In the Configure primary orchestrator section, enter the **Primary orchestrator name** and set a password in the **Orchestrator password** field. Confirm the password to secure access to the external orchestrator interface.

3. You should provide the **IBM Cloud API key**, and if it is valid then you can provide the remaining fields.

4. In the **Schematics workspace** field, select an appropriate workspace for the orchestrator. If required, create a [VPC landing zone](https://cloud.ibm.com/catalog/architecture/deploy-arch-ibm-pvs-inf-2dd486c7-b317-4aaa-907b-42671485ad96-global/readme/terraform/terraform/e104e91d-d4a8-44fa-a341-eebf735d9635-global) to define the Power Virtual Server workspace where the primary orchestrator will be deployed.

5. Provide either **Public SSH key** or Select from **Secrets Manager**.

6. Choose a **Public SSH key** and **IBM Cloud API key** from the **Secrets Manager** or upload new keys if necessary to ensure secure connections.

7. Expand the **Advanced Configuration** section to adjust additional settings for storage tiers and machine types, if applicable.

8. To enable **High Availability**, configure a Standby orchestrator name and select a **Secondary Power Virtual Server workspace** to define where the standby orchestrator will be deployed. These settings enable the orchestrator to provide continuous recovery capabilities if the primary site fails.

9. After verifying all settings, click **Deploy orchestrator** to start the deployment process, which creates the orchestrator VM.

10. Once the orchestrator is deployed, manage the service through the [**orchestrator interface**](https://10.32.150.93:3000/login?byCloud=true) and configure additional virtual server instances for disaster recovery.

11. If any issues occur during deployment, follow on-screen prompts to troubleshoot and retry the deployment.

By following this process, you ensure that your orchestrator is fully equipped to manage disaster recovery operations for your virtual servers. The **Orchestrator Details** and **Service Details** sections provide comprehensive technical insights that help administrators and cloud engineers monitor and manage disaster recovery automation for their infrastructure.

## Orchestrator details
{: #orc-det}

**Orchestrator instance identifier**
The unique identifier for the orchestrator instance is responsible for managing failover, failback, and replication processes between the primary and DR sites.

**Orchestrator health status**
Displays the current health and state of the orchestrator, such as "Running." The orchestrator must be operational for DR functions to be ready.

**IBM Cloud SSH key**
Refers to the secure IBM Cloud SSH key used for authenticated and encrypted communication between the orchestrator and the managed VMs involved in DR.

**Linked SSH Key for remote access**
Indicates the SSH key linked to the orchestrator for remote access to VMs. Proper configuration is crucial for secure VM operations.

**Infrastructure as Code (IaC) Environment**
The IaC environment automates the provisioning of DR resources, leveraging Terraform templates to define workflows for automation.

**Schematics workspace connection**
Shows whether the orchestrator is successfully connected to the Schematics workspace. A “Running” status indicates successful infrastructure automation.

## Service details
{: #service-det}

**Disaster recovery service configuration**
Identifies the DR service configured in IBM Cloud for the orchestrator, linking it to the correct DR environment.

**Data center location**
Specifies the region or data center, such as "Dallas 12," where the DR resources are hosted and where failover will occur.

**Resource group**
Displays the IBM Cloud resource group managing the DR resources, allowing for resource-level permissions and management.

**Globally unique identifier**
A globally unique identifier for the DR service within IBM Cloud, enabling resource tracking and auditing across cloud environments using APIs.
