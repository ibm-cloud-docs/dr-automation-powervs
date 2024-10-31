---
front_matter_title: "Generating an Estimate for DR Automation on IBM Power Virtual Server"
lastupdated: "2024-10-23"
copyright: "2023, 2024"
subcollection: dr-automation
---
# Generating an Estimate for DR Automation on IBM Power Virtual Server

Use the cost estimator tool to evaluate potential costs for DR Automation resources before deployment. This tool allows customization of configurations to align with your disaster recovery needs.

## Use the Cost Estimator Tool For

- Creating an estimate for DR automation resources
- Saving and reviewing your estimate
- Exporting estimates for record-keeping

---

## Steps to Generate an Estimate for DR Automation

### Step 1: Accessing the Cost Estimator

1. **Log in to IBM Cloud Catalog**  
   - Use your IBM credentials to access the IBM Cloud catalog.

2. **Select DR Automation for Power Virtual Server**  
   - In the search box, type **DR Automation for Power Virtual Server**.
   - Click on the **DR Automation for Power Virtual Server** tile.

---

### Step 2: Creating an Estimate for Resources

You can generate an estimate by specifying the necessary configurations for DR resources, such as the number of cores. This process allows you to review projected costs before making deployment decisions.

> **Note**: Creating an estimate incurs no charges. Resources are billed only upon deployment.

1. **Select the Location Type**  
   - Choose the **DR Automation setup** as it is hosted within IBM’s data centers.

2. **Configure DR-Specific Parameters**  
   - **Disaster Recovery Location**: Choose the IBM Cloud region where the DR resources will be hosted.
   - **Total Managed Cores**: Define the number of cores required for DR.
   - **Orchestrator HA**: Enable this option if high availability is needed for your orchestrator. Additional charges may apply.

---

### Step 3: Adding to Estimate and Viewing Summary

- **Add to Estimate**: Click **Add to estimate** to save your configured DR resources.
- Review the **Total Estimated Cost** on the right panel, which includes core-based charges for DR software licenses.

---

### Step 4: Saving and Viewing the Estimate

1. After configuring, save the estimate with a unique name and optional description.
2. **View Estimate**: Access your saved estimate to review the detailed cost breakdown.

---

### Step 5: Exporting the Estimate

1. **Download**: Export the saved estimate as an **XLSX**, **CSV**, or **PDF** file.
2. This allows for offline review and sharing with stakeholders.

---

## DR Automation Configuration Summary

| Field                          | Description                                                                                           |
|--------------------------------|-------------------------------------------------------------------------------------------------------|
| **Disaster Recovery Location**  | Select the IBM Cloud region for DR replication.                                                      |
| **Total Managed Cores**         | Define the number of cores necessary for your DR setup.                                             |
| **Orchestrator HA**             | Optional: Enable high availability for the orchestrator if required.                                |

---

## Creating, Saving, and Viewing an Estimate

1. **Add to Estimate**  
   - After configuring your DR Automation resources, click **Add to estimate**.

2. **Estimate Window Options**  
   - In the **Estimate** window, you can choose to add this configuration to an existing estimate or create a new one.
   - To create a new estimate, specify a name and optional description, then click **Create**.

3. **Save and View Estimate**  
   - Save your estimate, and you can view it anytime in the IBM Cloud console under **View estimate**. This provides a quick overview of your configured resources and estimated costs.

---

## Exporting the Estimate

- **Download**  
  - Click **Download** to export the saved estimate in **XLSX**, **CSV**, or **PDF** format.
  - This feature allows you to keep a record of your estimate and share it with relevant stakeholders for planning and budgeting.

This process ensures that customers have a clear understanding of DR Automation costs on Power Virtual Server, providing transparency and control over anticipated expenses.
