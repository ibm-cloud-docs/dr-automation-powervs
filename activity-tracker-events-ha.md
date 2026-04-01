---

copyright:
  years: 2025
lastupdated: "2026-04-01"

subcollection: dr-automation-powervs

keywords: events

---

# Activity tracker events for  PowerHA SystemMirror
{: #ate-for-dr-automation} 

Activity tracking events report on activities that change the state of a service in IBM Cloud. You can use the events to investigate abnormal activity and critical actions and to comply with regulatory audit requirements.
{:shortdesc: .shortdesc}

You can use IBM Cloud Activity Tracker Event Routing, a platform service, to route auditing events in your account to destinations of your choice by configuring targets and routes that define where activity tracking events are sent. For more information, see [Getting started tutorial for Activity Tracker Event Routing](https://cloud.ibm.com/docs/activity-tracker?topic=activity-tracker-getting-started).

You can use IBM Cloud Logs to visualize and alert on events that are generated in your account and routed by IBM Cloud Activity Tracker Event Routing to an IBM Cloud Logs instance.

> **Important**: As of <strong>28 March 2024</strong>, the IBM Cloud Activity Tracker service is deprecated and will no longer be supported as of <strong>30 March 2025</strong>. Customers will need to migrate to IBM Cloud Logs before <strong>30 March 2025</strong>. During the migration period, customers can use IBM Cloud Activity Tracker along with IBM Cloud Logs. Activity tracking events are the same for both services. For information about migrating from IBM Cloud Activity Tracker to IBM Cloud Logs and running the services in parallel, see [link_to_migration_planning](/docs/cloud-logs?topic=cloud-logs-migration-intro).

Activity Tracker Event Routing records user-initiated activities that change the state of a service in IBM Cloud. You can use this service to investigate abnormal activity and critical actions and to comply with regulatory audit requirements. In addition, you can be alerted about actions as they happen. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard. For more information, see the [Getting started tutorial for Activity Tracker Event Routing](/docs/activity-tracker?topic=activity-tracker-getting-started).

## Management events
{: #manag events} 

This document provides details on various events relevant to PowerHA SystemMirror. These events help administrators manage instance readiness, images, network configurations, and security policies required for effective disaster recovery.

## PowerHA SystemMirror service events documentation
{: #site events}

This document provides details of the key events and their respective API operations in the **PowerHA SystemMirror Service**.

## tracker events for PowerHA SystemMirror
{: #ate-for-powerha}

Activity tracking events report on activities that change the state of a service in IBM Cloud. You can use the events to investigate abnormal activity and critical actions and to comply with regulatory audit requirements.
{:shortdesc: .shortdesc}

You can use IBM Cloud Activity Tracker Event Routing, a platform service, to route auditing events in your account to destinations of your choice by configuring targets and routes that define where activity tracking events are sent.

You can use IBM Cloud Logs to visualize and alert on events that are generated in your account and routed by IBM Cloud Activity Tracker Event Routing to an IBM Cloud Logs instance.

> **Important**: As of <strong>28 March 2024</strong>, the IBM Cloud Activity Tracker service is deprecated and will no longer be supported as of <strong>30 March 2025</strong>. Customers must migrate to IBM Cloud Logs before <strong>30 March 2025</strong>.

Activity Tracker Event Routing records user-initiated activities that change the state of a service in IBM Cloud. The events comply with the Cloud Auditing Data Federation (CADF) standard.

---

## Management events
{: #manage-events-powerha}

This document provides details on various events relevant to PowerHA SystemMirror. These events help administrators manage and monitor high availability (HA) environments.

---

## PowerHA SystemMirror service events documentation
{: #powerha-events}

This section lists the key Activity Tracker events and their corresponding API operations for the **PowerHA SystemMirror service**.

---

## Dashboard
{: #dashboard-events}

| Action | Description |
|--------|------------|
| `power-dr-automation.dashboard.view` | View the PowerHA dashboard for the service instance. |
{: caption="dashboard" caption-side="bottom"}

---

## PowerHA settings
{: #powerha-settings-events}

| Action | Description |
|--------|------------|
| `power-dr-automation.powerha-settings.read` | Retrieve PowerHA configuration settings for the service instance. |
| `power-dr-automation.powerha-settings.update` | Update PowerHA configuration settings for the service instance. |
{: caption="powerha-settings" caption-side="bottom"}

---

## PowerHA operation
{: #powerha-operation-events}

| Action | Description |
|--------|------------|
| `power-dr-automation.powerha-operation.read` | Retrieve PowerHA operational details for the service instance. |
{: caption="powerha-operation" caption-side="bottom"}

---

## PowerHA summary
{: #powerha-summary-events}

| Action | Description |
|--------|------------|
| `power-dr-automation.powerha-summary.read` | Retrieve summary information for PowerHA environments. |
{: caption="powerha-summary" caption-side="bottom"}

---

## Event
{: #powerha-event-events}

| Action | Description |
|--------|------------|
| `power-dr-automation.powerha-event.list` | Retrieve a list of PowerHA events. |
| `power-dr-automation.powerha-event.read` | Retrieve details of a specific PowerHA event. |
{: caption="powerha-event" caption-side="bottom"}

---

## PowerHA virtual machines
{: #powerha-vm-events}

| Action | Description |
|--------|------------|
| `power-dr-automation.powerha-vm.read` | Retrieve information about PowerHA-managed virtual machines. |
| `power-dr-automation.powerha-vm.update` | Update PowerHA-managed virtual machine configuration. |
{: caption="powerha-vm" caption-side="bottom"}

## Viewing PowerHA SystemMirror events
{: #view}

PowerHA SystemMirror events are automatically forwarded to specific geographic locations based on data center regions. You can access the activity tracker logs for PowerHA SystemMirror as follows:

- All North America and South America data centers from Dallas.
- All Europe data centers from Frankfurt.
- All Sydney data center from Sydney.
- All Japan data center from Tokyo.

For a comprehensive list of locations where PowerHA SystemMirror
 events are enabled to send logs to IBM Cloud Logs, see [IBM Cloud services that generate Activity Tracker events](https://cloud.ibm.com/docs/activity-tracker?topic=activity-tracker-cloud_services_locations&interface=cli#cloud_services_locations_power-iaas).

The Activity Tracker service supports only one instance per location. To view {{site.data.keyword.DR_short}}
 events, you must access the Activity Tracker web UI in the same location where your HA service instance is deployed. For additional guidance, see [Launching the web UI through the IBM Cloud UI](https://cloud.ibm.com/docs/activity-tracker?topic=activity-tracker-launch).

## Activity tracker sample response format
{: #at tracker}

The new response format that is used in activity tracking adheres to the CADF (Cloud Auditing Data Federation) standard. Hence, auditing events can be collected and routed in a standardized format, ensuring consistency and interoperability across different cloud platforms.

> **Note**: The CADF standard is significant in auditing security in cloud environments. It defines a comprehensive event model that includes the necessary information for certifying, managing, and auditing the security of applications and services in the cloud.

The following code snippets show the differences between the old and new activity tracker response format.

### Log message
{: #log msg}

```json
{
  "Time": "2026-03-19T06:27:45.396909981Z",
  "line": {
    "action": "power-dr-automation.powerha-operation.read",
    "correlationId": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
    "dataEvent": false,
    "eventTime": "2026-03-19T06:27:44.90+0000",
    "initiator": {
      "authnId": "IBMid-xxxxxxxx",
      "authnName": "xxxxxxxx xxxxxxxx",
      "credential": {
        "type": "user"
      },
      "host": {
        "address": "127.0.0.1",
        "addressType": "IPv4",
        "agent": "PostmanRuntime/x.x.x"
      },
      "id": "IBMid-xxxxxxxx",
      "name": "xxxxxxxx@xxxx.com",
      "typeURI": "service/security/account/user"
    },
    "logSourceCRN": "crn:v1:staging:public:power-dr-automation:global:a/xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx::",
    "message": "disaster-recovery-service: read powerha-operation",
    "observer": {
      "name": "ActivityTracker"
    },
    "outcome": "success",
    "reason": {
      "reasonCode": 200,
      "reasonType": "OK"
    },
    "requestData": {},
    "responseData": {
      "dr_locations": [
        { "id": "wdc07", "name": "Washington DC 07" },
        { "id": "wdc06", "name": "Washington DC 06" },
        { "id": "us-south", "name": "Dallas 13" },
        { "id": "us-east", "name": "Washington DC" },
        { "id": "tor01", "name": "Toronto 01" },
        { "id": "tok04", "name": "Tokyo 04" },
        { "id": "syd05", "name": "Sydney 05" },
        { "id": "syd04", "name": "Sydney 04" },
        { "id": "sao05", "name": "Sao Paulo 05" },
        { "id": "sao04", "name": "Sao Paulo 04" },
        { "id": "sao01", "name": "Sao Paulo 01" },
        { "id": "osa21", "name": "Osaka 21" },
        { "id": "mon01", "name": "Montreal 01" },
        { "id": "mad04", "name": "Madrid 04" },
        { "id": "mad02", "name": "Madrid 02" },
        { "id": "lon06", "name": "London 06" },
        { "id": "lon04", "name": "London 04" },
        { "id": "eu-de-2", "name": "Frankfurt 05" },
        { "id": "eu-de-1", "name": "Frankfurt 04" },
        { "id": "dal14", "name": "Dallas 14" },
        { "id": "dal12", "name": "Dallas 12" },
        { "id": "dal10", "name": "Dallas 10" },
        { "id": "che02", "name": "Chennai 02" },
        { "id": "che01", "name": "Chennai 01" }
      ]
    },
    "saveServiceCopy": true,
    "severity": "normal",
    "target": {
      "id": "crn:v1:staging:public:power-dr-automation:global:a/xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx::",
      "name": "",
      "resourceGroupId": "",
      "typeURI": "power-dr-automation/powerha-operation"
    }
  },
  "Hostname": "xxxxxxxxxxxxxxxxxxxxxxxxxxxx",
  "AdditionalContext": "context"
}
```


## Activity tracker regions
{: #at trackerregions}

You can create an activity tracker instance and provision it in the same region where your data center is located.

> **Important:** The PowerHA SystemMirror workspaces that run in various regions or data centers will send events to activity tracker instances in their respective regions effective from 29 January 2024. You must create and provision instances of activity tracker in the respective regions where your workspaces reside for continued access to PowerHA SystemMirror activity tracker events. If you want to export activity tracker events, see [Exporting Activity Tracker events](https://cloud.ibm.com/docs/activity-tracker?topic=activity-tracker-export).

The following table shows the data center and its corresponding regions where you can deploy an activity tracker instance:

## Data center
{: #data-cents}

| Datacenter | Activity Tracker Region |
|------------|-------------------------|
| WDC04      | us-east                 |
| WDC06      | us-east                 |
| WDC07      | us-east                 |
| MON01      | ca-tor                  |
| TOR04      | ca-tor                  |
| SAO01      | br-sao                  |
| SAO04      | br-sao                  |
| LON04      | eu-gb                   |
| LON06      | eu-gb                   |
| OSA21      | jp-osa                  |
{: caption="List of DCs and their corresponding AT instance region" caption-side="bottom"}
