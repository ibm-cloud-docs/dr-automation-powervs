---
copyright:
  years: 2025
lastupdated: "2026-04-16"

subcollection: dr-automation-powervs

keywords: create instance

---

# Create an instance for {{site.data.keyword.DR_full_notm}}
{: #cinstance}

Creating an instance for {{site.data.keyword.DR_full}} in IBM Cloud allows you to set up disaster recovery and high availability configurations, including resource allocation and high availability options. This instance serves as a failover mechanism in a disaster recovery event. By following the procedure below, you can deploy the orchestrator with the necessary configurations to meet your disaster recovery requirements.
{:shortdesc: .shortdesc}

## Procedure
{: #procedure}

Follow these steps to create a Power Virtual Server instance for {{site.data.keyword.DR_short}}:

1. Log in to the [**IBM Cloud catalog**](https://cloud.ibm.com/catalog) with your credentials.

2. In the **search box**, type {{site.data.keyword.DR_full_notm}} and click the corresponding tile.

3. Select the location from the drop-down list.
   Select the deployment type **PowerVS DR Automation** or **PowerVS Private Cloud support** or **PowerHA AIX for PowerVS** for the pricing plan.

   **Note:**
   - If you select **PowerVS Private Cloud support**, a Managed VM for disaster recovery is provisioned within your PowerVS workspace.
   - To enable this feature, ensure that you have at least one PowerVS workspace available in your location. When you select this plan in the External Orchestrator UI, a list of available workspaces is displayed.
   - From the list, choose the appropriate workspace and enable the workload that you want to protect with disaster recovery.

4. In the **Configure your resource** section, provide a name for the instance and select the appropriate resource group.
   - You can create a new resource group if needed by clicking **Create resource group**.

5. *(Optional)* Add user tags for better instance management (for example, `env:dev`, `version-1`) and, Add **Access management tags** to control IAM access.

6. To enable High Availability (HA) for the PowerVS DR Automation orchestrator, check that the box labeled Deploy orchestrator with HA. The Deploy orchestrator with HA option can be enabled only through the PowerVS DR Automation pricing plan.

   > **Note:** If you select **Deploy orchestrator with HA**, two virtual machines are created—one as the primary and the other as a standby for disaster recovery events.

7. Enter all the necessary information, review the details and click **Create resource**.

8. You are redirected to the **Service details** page, where you can manage your newly created DR instance.

For more information about the appropriate region for your workspace, see [IBM Cloud regions](https://cloud.ibm.com/docs/overview?topic=overview-locations).
