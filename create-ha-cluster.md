---
copyright:
  years: 2025
lastupdated: "2026-02-24"

subcollection: dr-automation-powervs

keywords: create instance for PowerHA , powerha instance, add node

---

# Creating HA cluster
{: #creating-ha-cluster}


## Create HA cluster
{: #create-ha-cluster}

After creating the service instance, configuring the HA cluster in {{site.data.keyword.DR_full}} is required to enable high availability for your Power Virtual Server environment. The HA cluster establishes coordinated nodes that help ensure workload continuity during planned or unplanned outages. This screen allows you to configure the location, workspace, API authentication key, and related high availability settings. Once configured, {{site.data.keyword.DR_short}} supports automatic failover and resilient operations to maintain service availability.
{:shortdesc: .shortdesc}

## Procedure
{: #procedure-ha-cluster}

To configure the HA cluster, complete the following steps:

1. On the **Service details** page, in the **HA cluster** section, click **Edit**.
2. In the **Edit configuration** panel, enter the required **API key** and validate it.
3. Select the **High availability location**.
4. Select the appropriate **Power Virtual Server workspace**.
5. Click **Save** to apply the configuration.

## Add Node
{: #add-node}

After you complete the HA cluster configuration, add nodes to the cluster.

## Procedure
{: #procedur-add-node}

To add nodes, complete the following steps:

1. On the **Service details** page, scroll to the **Cluster nodes** section.
2. Click **Add node**.
3. In the **Add nodes** panel, review the following details:
   - **High availability location**
   - **Power Virtual Server workspace name**
   - **Power Virtual Server workspace ID**

4. From the list of available virtual server instances, select the nodes that you want to add to the cluster.
   You can review details such as:
   - **Name**
   - **ID**
   - **IPs**
   - **Cores**
   - **Memory**
   - **Status**

5. Click **Add instance** to add the selected nodes to the cluster.

After the nodes are added, they appear in the **Cluster nodes** table, where you can monitor their status and continue with agent installation and failover configuration.
