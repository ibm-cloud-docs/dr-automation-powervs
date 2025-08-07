---
copyright:
  years: 2025
lastupdated: "2025-07-30"

subcollection: dr-automation

keywords: create instance

---

# Create an instance for {{site.data.keyword.DR_full_notm}}
{: #cinstance}

Creating an instance for {{site.data.keyword.DR_full_notm}} in IBM Cloud allows you to set up disaster recovery configurations, including resource allocation and high availability options. This instance serves as a failover mechanism in case of a disaster recovery event. By following the procedure below, you can deploy the orchestrator with the necessary configurations to meet your disaster recovery requirements.
{:shortdesc: .shortdesc}

## Procedure
{: #procedure}

Follow these steps to create a Power Virtual Server instance for disaster recovery:

1. Log in to the [**IBM Cloud catalog**](https://cloud.ibm.com/catalog) with your credentials.
2. In the **search box**, type {{site.data.keyword.DR_full}} and click the corresponding tile.
3. Select the Disaster Recovery location from the drop-down list. Choose **IBM Cloud** or **Client location**, depending on your deployment model.
   

 > **Note**: If you select Client location, a Managed VM for disaster recovery is provisioned within your PowerVS workspace.
 > To enable this feature, ensure that you have at least one PowerVS workspace available in your location.
 > When you select this plan in the VMRM UI, a list of available workspaces is displayed.
 > From the list, you can choose the appropriate workspace and enable the workload you want to protect with disaster recovery.

4. In the Configure details section, provide a name for the instance and select the appropriate resource group.
   - You can create a new resource group if needed by clicking **Create resource group**.
5. *(Optional)* You can add user tags for better instance management (e.g., `env:dev`, `version-1`).
6. If you want to enable **High Availability(HA)** for the orchestrator, check the box labeled **Deploy orchestrator with HA**.
   > **Note**: If you select **Deploy orchestrator with HA**, two virtual machines will be created—one as the primary and the other as a standby for disaster recovery events.
7. Once you've entered all the necessary information, review the details and **click** Create Resource.
8. You will be redirected to the **Service details** page, where you can manage your newly created DR instance.

For more information about the appropriate region for your workspace, see [IBM Cloud regions](https://cloud.ibm.com/docs/overview?topic=overview-locations).
