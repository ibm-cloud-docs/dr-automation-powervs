---
front_matter_title: "Monitoring metrics for IBM DR Automation"
lastupdated: "2024-10-23"
copyright: "2023, 2024"
subcollection: dr-automation
---
# Monitoring metrics for IBM DR Automation

Create an IBM Cloud Monitoring instance and enable the platform metrics to capture various performance metrics.

## Steps to Create an IBM cloud monitoring instance

To monitor platform metrics, select the region where your Power Virtual Server workspace is provisioned.

1. Log in to the [IBM Cloud console](https://cloud.ibm.com/).
2. Search for **IBM Cloud Monitoring** and select it.
3. Select your location and enter your custom values for the **Service name** field and other fields.
4. Select the **Enable** indicator for IBM platform metrics.
5. Select the license agreements indicator and click **Create**.

You can also create the IBM Cloud Monitoring instance from the **Integration (Optional)** section when you create a workspace, if no IBM Cloud Monitoring instance is already created for that region.

## Viewing metrics

To view the metrics dashboards, access the user interface of IBM Cloud Monitoring in the following ways:

- Access the IBM Cloud Monitoring user interface from your [**DR Automation for PowerVS**](#accessing-metrics-from-dr-automation-workspace) workspace.
- Access the IBM Cloud Monitoring user interface from the [**Observability**](#accessing-metrics-from-the-observability-page) page.

To view metrics in your dashboard, you must enable the platform metrics of the IBM Cloud Monitoring instance.

### Accessing metrics from DR Automation workspace

From the left navigation menu of the Power Virtual Server user interface, complete the following steps:

1. Click **Workspaces**.
2. Select the workspace for which a monitoring instance is available.
3. From the workspace details page, click **Launch monitoring**. The IBM Cloud Monitoring dashboard opens.
4. Click **Dashboards > Dashboard Library > IBM** and select your dashboard to view.

### Accessing metrics from the observability page

To access the dashboard, complete the following steps:

1. Log in to the [IBM Cloud console](https://cloud.ibm.com/login).
2. Expand the left navigation window.
3. Click **Resource list**.
4. Click **Observability > Monitoring**.
5. Click the instance.
6. Click **Open dashboard**. The IBM Cloud Monitoring dashboard opens.
7. Click **Dashboards > Dashboard Library > IBM** and select your dashboard to view.

## Additional information

- See the [IBM Cloud Monitoring documentation](https://cloud.ibm.com/docs/monitoring) in IBM Cloud.
