---
copyright:
  years: 2025
lastupdated: "2025-01-16"

subcollection: dr-automation

keywords: price

---

# Generating an estimate for {{site.data.keyword.DR_full_notm}}
{: #pricec}

Use the cost estimator tool to evaluate potential costs for DR Automation resources before deployment. This tool allows customization of configurations to align with your disaster recovery needs.
{:shortdesc: .shortdesc}

## Use the cost estimator tool for
{: #uce}

- Creating an estimate for DR automation resources
- Saving and reviewing your estimate
- Exporting estimates for record-keeping


## Steps to generate an estimate for DR Automation
{: #stg}

### Step 1: Accessing the cost estimator
{: #accst}

- Use your IBM credentials to access the **IBM Cloud catalog**.

- In the **search box**, type IBM {{site.data.keyword.DR_full}}.

- **Click** {{site.data.keyword.DR_full_notm}} tile.


### Step 2: Creating an estimate for resources
{: #createst}

You can generate an estimate by specifying the necessary **configurations** for DR resources, such as the number of **cores**. This process allows you to review projected costs before making deployment decisions.

> **Note**: Creating an estimate incurs no charges, resources are billed only upon deployment.

- Choose the **{{site.data.keyword.DR_short}}** setup as it is hosted within IBM’s data centers.

- Choose the **IBM Cloud region** where the DR resources will be hosted.

- Define the number of cores required for DR.

- Enable **Orchestrator HA** option if high availability is needed for your orchestrator. Additional charges may apply.


### Step 3: Adding to estimate and viewing summary
{: #stps}

- Click **Add** to estimate to **save** your configured DR resources.
- Review the Total Estimated Cost on the right panel, which includes core-based charges for DR software licenses.


### Step 4: Saving and viewing the estimate
{: #stepss}

- After configuring, **save** the estimate with a **unique name** and optional description.
- Access your saved estimate to review the detailed cost breakdown.


### Step 5: Exporting the estimate
{: #ete}

- Export the saved estimate as an **XLSX**, **CSV**, or **PDF** file.

- This allows for offline review and sharing with stakeholders.


## {{site.data.keyword.DR_short}} configuration summary
{: #drcs}

| Field                          | Description                                                                                           |
|--------------------------------|-------------------------------------------------------------------------------------------------------|
| Disaster Recovery Location  | Select the IBM Cloud region for DR replication.                                                      |
| Total Managed Cores         | Define the number of cores necessary for your DR setup.                                             |
| Orchestrator HA             | Optional: Enable high availability for the orchestrator if required.                                |
Configuration Parameters for {{site.data.keyword.DR_short}}
{: caption="configuration summary" caption-side="bottom"}

## Creating, Saving, and viewing an estimate
{: #csve}

1. After configuring your DR Automation resources, click **Add to estimate**.

2. In the Estimate window, you can choose to add this configuration to an existing estimate or **create** a new one.
3. To **create** a new estimate, specify a name and optional description, then click **Create**.

4. **Save** your estimate, and you can view it anytime in the IBM Cloud console under View estimate, 
this provides a quick overview of your configured resources and estimated costs.


## Exporting the estimate
{: #est}

1. Click Download to export the saved estimate in **XLSX**, **CSV**, or **PDF** format.
2. This feature allows you to keep a record of your estimate and share it with relevant stakeholders for planning and budgeting.

This process ensures that customers have a clear understanding of DR Automation costs on Power Virtual Server, providing transparency and control over anticipated expenses.
