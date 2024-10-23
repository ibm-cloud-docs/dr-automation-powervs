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

1. After completing the Create resource step, click Manage to proceed with the deployment.

2. In the Enable network connectivity section, verify that all network connectivity prerequisites are   fulfilled by creating a [VPC landing zone](https://cloud.ibm.com/catalog/architecture/deploy-arch-ibm-pvs-inf-2dd486c7-b317-4aaa-907b-42671485ad96-global/readme/terraform/terraform/e104e91d-d4a8-44fa-a341-eebf735d9635-global) and selecting the required schematics workspace.

3. You can choose a Public SSH key and IBM Cloud API key from Secrets Manager or upload new keys if necessary.

4. For HA configuration, select the secondary Power Virtual Server workspace for high availability, if applicable.

5. To enable high availability for the orchestrator, check the box for Deploy orchestrator with HA.

6. In the Configure Orchestrator login section, enter and confirm a password to secure the external orchestrator interface.

7. In the Advanced Configuration section, To create the VM, select the appropriate Storage tier and Machine type for your orchestrator.

8. Review your selections carefully.

9. Click Re-deploy orchestrator to begin the deployment process which creates the orchestrator VM.

10. Once the orchestrator is deployed, manage the service through the VMRM DR PowerVS orchestrator interface and configure additional virtual server instances for disaster recovery.

11. If any errors occur during deployment, follow the prompts to retry the deployment.
