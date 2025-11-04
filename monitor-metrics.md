---
copyright:
  years: 2025
lastupdated: "2025-11-04"

subcollection: dr-automation-powervs

keywords: monitor

---

# Monitoring metrics for IBM DR Automation
{: monitor met-ibm}

Create an IBM Cloud Monitoring instance and enable the platform metrics to capture various performance metrics.
{:shortdesc: .shortdesc}

## Steps to Create an IBM cloud monitoring instance
{: instance}

To monitor platform metrics, select the region where your Power Virtual Server workspace is provisioned.

1. Log in to the [IBM Cloud console](https://cloud.ibm.com/).
2. Search for **IBM Cloud Monitoring** and select it.
3. Select your location and enter your custom values for the **Service name** field and other fields.
4. Select the **Enable** indicator for IBM platform metrics.
5. Select the license agreements indicator and click **Create**.

You can also create the IBM Cloud Monitoring instance from the **Integration (Optional)** section when you create a workspace, if no IBM Cloud Monitoring instance is already created for that region.

## Viewing metrics
{: view-metrics}

To view the metrics dashboards, access the user interface of IBM Cloud Monitoring in the following ways:

- Access the IBM Cloud Monitoring user interface from your [**DR Automation for PowerVS**](#accessing-metrics-from-dr-automation-workspace) workspace.
- Access the IBM Cloud Monitoring user interface from the [**Observability**](#accessing-metrics-from-the-observability-page) page.

To view metrics in your dashboard, you must enable the platform metrics of the IBM Cloud Monitoring instance.

### Accessing metrics from DR Automation workspace
{: metrics-workspace}

From the left navigation menu of the Power Virtual Server user interface, complete the following steps:

1. Click **Workspaces**.
2. Select the workspace for which a monitoring instance is available.
3. From the workspace details page, click **Launch monitoring**. The IBM Cloud Monitoring dashboard opens.
4. Click **Dashboards > Dashboard Library > IBM** and select your dashboard to view.

### Accessing metrics from the observability page
{: access-metric}

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


## Metrics available by service plan
{: metrics-by-plan}

| Metric Name |
|-----------|
| [Number of Managed VMs](#ibm_power_dr_automation_managed_vm_count) | 
{: caption="Metrics Available by Plan Names" caption-side="top"}

### Number of Managed VMs count
{: #ibm_power_dr_automation_managed_vm_count}

| Metadata | Description |
|----------|-------------|
| `Metric Name` | `ibm_power_dr_automation_managed_vm_count`|
| `Metric Type` | `gauge` |
| `Value Type`  | `count` |
| `Segment By` | `Service instance, Service instance name` |
{: caption=" Number of Managed VMs metric metadata" caption-side="top"}

## Attributes for Segmentation
{: attributes}

The following attributes are available for segmenting all of the metrics listed above

### Global attributes
{: global-attributes}

| Attribute | Attribute Name | Attribute Description |
|-----------|----------------|-----------------------|
| `Cloud Type` | `ibm_ctype` | The cloud type is a value of public, dedicated or local |
| `Location` | `ibm_location` | The location of the monitored resource - this may be a region, data center or global |
| `Resource` | `ibm_resource` | The resource being measured by the service - typically a indentifying name or GUID |
| `Resource Type` | `ibm_resource_type` | The type of the resource being measured by the service |
| `Resource group` | `ibm_resource_group_name` | The resource group where the service instance was created |
| `Scope` | `ibm_scope` | The scope is the account, organization or space GUID associated with this metric |
| `Service name` | `ibm_service_name` | Name of the service generating this metric |
{: caption="Segmenting all of the Metrics" caption-side="top"}

### Additional attributes
{: additional-attributes}

The following attributes are available for segmenting one or more attributes as described in the reference above. Please see the individual metrics for segmentation options.


| Attribute | Attribute Name | Attribute Description |
|-----------|----------------|-----------------------|
| `Service instance` | `ibm_service_instance` | The service instance segment identifies the instance the metric is associated with |
| `Service instance name` | `ibm_service_instance_name` | The service instance name provides the user-provided name of the service instance which isn't necessarily a unique value depending on the name provided by the user. |
{: caption="Segmentation options" caption-side="top"}
