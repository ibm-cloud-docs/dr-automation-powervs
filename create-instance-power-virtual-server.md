---
title: "Create an instance for Power Virtual Server"
lastupdated: "2024-10-23"
---

# Create an instance for Power Virtual Server {: #create-instance-power-virtual-server }

Creating an instance for Power Virtual Server in IBM Cloud allows you to set up disaster recovery configurations, including resource allocation and high availability options. This instance serves as a failover mechanism in case of a disaster recovery event. By following the procedure below, you can deploy the orchestrator with the necessary configurations to meet your disaster recovery requirements.

## Procedure {: #procedure }

Follow these steps to create a Power Virtual Server instance for disaster recovery:

1. Log in to the IBM Cloud catalog with your credentials.
2. In the search box, type **DR Automation for Power Virtual Server** and click the corresponding tile.
3. Select the **Disaster Recovery location** from the drop-down list.
   - This is where the virtual server instances will replicate for disaster recovery.
4. In the **Configure details** section, provide a name for the instance and select the appropriate resource group.
   - You can create a new resource group if needed by clicking **Create resource group**.
5. (Optional) You can add user tags for better instance management (e.g., `env:dev`, `version-1`).
6. If you want to enable high availability for the orchestrator, check the box labeled **Deploy orchestrator with HA**.
   > **Note**: If you select **Deploy orchestrator with HA**, two virtual machines will be created—one as the primary and the other as a standby for disaster recovery events.
7. Once you've entered all the necessary information, review the details and click **Create Resource**.
8. You will be redirected to the **Workspaces** page, where you can manage your newly created DR instance.

For more information about the appropriate region for your workspace, see [IBM Cloud regions](https://cloud.ibm.com/docs/overview?topic=overview-locations).
