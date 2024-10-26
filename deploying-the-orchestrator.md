---
front_matter_title: "Deploying the Orchestrator"
lastupdated: "2024-10-23"
copyright: "2023, 2024"
subcollection: dr-automation
---

# Deploying the orchestrator

After creating the resource deploying the orchestrator for DR Automation is critical in ensuring your Power Virtual Server environment is protected against disaster events. The orchestrator coordinates disaster recovery operations, including replication, failover, and failback of virtual machines. On this screen, you will configure the orchestrator's network connectivity, **high availability (HA)** settings, authentication keys, and resource allocation. Once deployed, the orchestrator can manage multiple virtual servers and ensure continuous availability.

## Procedure {: #procedure }

Following the procedure below, you can deploy the orchestrator with the necessary configurations to meet your disaster recovery requirements.

1. After completing the Create resource step, click **Manage** to proceed with the deployment.

2. In the **Configure primary orchestrator** section, enter the **Primary orchestrator name** and set a password in the **Orchestrator password** field. Confirm the password to secure access to the external orchestrator interface.

3. In the **Schematics workspace** field, select an appropriate workspace for the orchestrator. If required, create a [VPC landing zone](https://cloud.ibm.com/catalog/architecture/deploy-arch-ibm-pvs-inf-2dd486c7-b317-4aaa-907b-42671485ad96-global/readme/terraform/terraform/e104e91d-d4a8-44fa-a341-eebf735d9635-global) to define the Power Virtual Server workspace where the primary orchestrator will be deployed.

4. Choose a **Public SSH key** and **IBM Cloud API key** from the **Secrets Manager** or upload new keys if necessary to ensure secure connections.

5. Expand the **Advanced Configuration** section to adjust additional settings for storage tiers and machine types, if applicable.

6. To enable high availability, configure a **Standby orchestrator name** and select a **Secondary Power Virtual Server workspace** to define where the standby orchestrator will be deployed. These settings enable the orchestrator to provide continuous recovery capabilities if the primary site fails.

7. After verifying all settings, click **Deploy orchestrator** to start the deployment process, which creates the orchestrator VM.

8. Once the orchestrator is deployed, manage the service through the [**VMRM DR PowerVS orchestrator interface**](https://ibmdocs-test.dcs.ibm.com/docs/en/vmrm-dr-powervs_test) and configure additional virtual server instances for disaster recovery.

9. If any issues occur during deployment, follow on-screen prompts to troubleshoot and retry the deployment.

By following this process, you ensure that your orchestrator is fully equipped to manage disaster recovery operations for your virtual servers, providing a resilient environment that supports business continuity in case of unforeseen events.
