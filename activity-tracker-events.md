---
front_matter_title: "Activity tracker events"
lastupdated: "2024-10-23"
copyright: "2023, 2024"
subcollection: dr-automation
---
# Activity tracker events

Activity tracking events report on activities that change the state of a service in IBM Cloud. You can use the events to investigate abnormal activity and critical actions and to comply with regulatory audit requirements.

You can use IBM Cloud Activity Tracker Event Routing, a platform service, to route auditing events in your account to destinations of your choice by configuring targets and routes that define where activity tracking events are sent. For more information, see [Getting started tutorial for Activity Tracker Event Routing](https://cloud.ibm.com/docs/activity-tracker?topic=activity-tracker-getting-started).

You can use IBM Cloud Logs to visualize and alert on events that are generated in your account and routed by IBM Cloud Activity Tracker Event Routing to an IBM Cloud Logs instance.

> **Important**: As of <strong>28 March 2024</strong>, the IBM Cloud Activity Tracker service is deprecated and will no longer be supported as of <strong>30 March 2025</strong>. Customers will need to migrate to IBM Cloud Logs before <strong>30 March 2025</strong>. During the migration period, customers can use IBM Cloud Activity Tracker along with IBM Cloud Logs. Activity tracking events are the same for both services. For information about migrating from IBM Cloud Activity Tracker to IBM Cloud Logs and running the services in parallel, see [link_to_migration_planning](/docs/cloud-logs?topic=cloud-logs-migration-intro).

Activity Tracker Event Routing records user-initiated activities that change the state of a service in IBM Cloud. You can use this service to investigate abnormal activity and critical actions and to comply with regulatory audit requirements. In addition, you can be alerted about actions as they happen. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard. For more information, see the [Getting started tutorial for Activity Tracker Event Routing](/docs/activity-tracker?topic=activity-tracker-getting-started).

## Management events

This document provides details on various events relevant to {{site.data.keyword.DR_short}}. These events help administrators manage instance readiness, images, network configurations, and security policies required for effective disaster recovery.

## {{site.data.keyword.DR_full}} Service Events Documentation

This document provides details of the key events and their respective API operations in the **{{site.data.keyword.DR_short}} Service**. Use the given screenshots as a reference for style and formatting.

## 1. cloud-instance

| Action                                    | Description                                             |
|-------------------------------------------|---------------------------------------------------------|
| `power-dr-automation.cloud-instance.modify` | Modify an existing service instance for DR automation.   |


## 2. Validate-dr

| Action                                   | Description                                              |
|------------------------------------------|----------------------------------------------------------|
| `power-dr-automation.validate-dr.read`   | Fetch all DR validation events from a specified timestamp. |


## 3. Region

| Action                                | Description                                                 |
|---------------------------------------|-------------------------------------------------------------|
| `power-dr-automation.region.read`     | Retrieve tunable settings for DR automation by region ID.    |


## 4. dr-operation

| Action                                   | Description                                           |
|------------------------------------------|-------------------------------------------------------|
| `power-dr-automation.dr-operation.read` | Create and manage a DR service instance.             |


## 5. dr-summary

| Action                                   | Description                                       |
|------------------------------------------|---------------------------------------------------|
| `power-dr-automation.dr-summary.read`   | Manage and access KSYS metering data.            |


## 6. manage-dr

| Action                                   | Description                                                |
|------------------------------------------|------------------------------------------------------------|
| `power-dr-automation.manage-dr.read`    | Add a new tenant to the DR automation system.              |


## 7. event

| Action                                   | Description                                                |
|------------------------------------------|------------------------------------------------------------|
| `power-dr-automation.event.list`        | Retrieve a list of all event logs from the DR automation system. |
| `power-dr-automation.event.read`        | Access specific event details for auditing and troubleshooting. |


## 8. KSYS

| Action                                   | Description                                                |
|------------------------------------------|------------------------------------------------------------|
| `power-dr-automation.ksys.put`          | Add a new KSYS instance to the DR automation system.       |
| `power-dr-automation.ksys.read`         | Retrieve information about existing KSYS instances.        |


## Viewing {{site.data.keyword.DR_short}} events

Disaster Recovery (DR) Automation events are automatically forwarded to specific geographic locations based on data center regions. You can access the activity tracker logs for {{site.data.keyword.DR_short}} as follows:

- All North America and South America data centers from Dallas.
- All Europe data centers from Frankfurt.
- All Sydney data center from Sydney.
- All Japan data center from Tokyo.

For a comprehensive list of locations where {{site.data.keyword.DR_short}}
 events are enabled to send logs to IBM Cloud Logs, see [IBM Cloud services that generate Activity Tracker events](https://cloud.ibm.com/docs/activity-tracker?topic=activity-tracker-cloud_services_locations&interface=cli#cloud_services_locations_power-iaas).

The Activity Tracker service supports only one instance per location. To view {{site.data.keyword.DR_short}}
 events, you must access the Activity Tracker web UI in the same location where your DR service instance is deployed. For additional guidance, see [Launching the web UI through the IBM Cloud UI](https://cloud.ibm.com/docs/activity-tracker?topic=activity-tracker-launch).

## Activity tracker sample response format

The new response format that is used in activity tracking adheres to the CADF (Cloud Auditing Data Federation) standard. Hence, auditing events can be collected and routed in a standardized format, ensuring consistency and interoperability across different cloud platforms.

> **Note**: The CADF standard is significant in auditing security in cloud environments. It defines a comprehensive event model that includes the necessary information for certifying, managing, and auditing the security of applications and services in the cloud.

The following code snippets show the differences between the old and new activity tracker response format.

### Log message

```json
{
    "logSourceCRN": "crn:v1:staging:public:pvs-dr-auto-cap-vmrm-grs4:global:a/dxxxxxxxxx:8c77xxx-c2xx-43xx-bac9-d1exxd7b2ecxxx::",
    "saveServiceCopy": true,
    "dataEvent": false,
    "outcome": "success",
    "eventTime": "2024-11-07T08:35:23.62+0000",
    "action": "dr-service-broker.provision.create",
    "correlationId": "23b8916b-39be-49fa-82f2-9e0eaf78a32e",
    "severity": "normal",
    "initiator": {
        "id": "admin",
        "name": "xxxxm@us.ibm.com",
        "typeURI": "service/security/account/user",
        "authnId": "",
        "authnName": "",
        "host": {
            "agent": "curl/7.61.1",
            "address": "127.0.0.1",
            "addressType": "IPv4"
        },
        "credential": {
            "type": "user"
        }
    },
    "target": {
        "id": "crn:v1:staging:public:pvs-dr-auto-cap-vmrm-grs4:global:a/xxxx6ca48d5f4b2899c26829b5e0xxxx:8c77xxxx-c2xx-43xx-baxx-d1e19xxxxec5556::",
        "name": "disaster-recovery-service",
        "typeURI": "dr-service-broker/provision",
        "resourceGroupId": ""
    },
    "reason": {
        "reasonCode": 200,
        "reasonType": "OK"
    },
    "requestData": null,
    "responseData": {
        "dashboard_url": "https://dra-ui-dev.1lcv1smi8d9z.us-south.codeengine.appdomain.cloud/overview?instance_id=crn:v1:staging:public:pvs-dr-auto-cap-vmrm-grs4:global:a/d8ab6ca48d5f4b2899c26829b5e0e304:8c77c634-c2cf-4313-bac9-d1e19d7b2ec5556::"
    },
    "message": "disaster-recovery-service: create provision disaster-recovery-service",
    "observer": {
        "name": "ActivityTracker"
    }
}
```


## Activity tracker regions

You can create an activity tracker instance and provision it in the same region where your data center is located.

> **Important:** The {{site.data.keyword.DR_short}} workspaces that run in various regions or data centers will send events to activity tracker instances in their respective regions effective from 29 January 2024. You must create and provision instances of activity tracker in the respective regions where your workspaces reside for continued access to {{site.data.keyword.DR_short}}
 activity tracker events. If you want to export activity tracker events, see [Exporting Activity Tracker events](https://cloud.ibm.com/docs/activity-tracker?topic=activity-tracker-export).

The following table shows the data center and its corresponding regions where you can deploy an activity tracker instance:

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
<<<<<<< Updated upstream
{: caption="List of DCs and their corresponding AT instance region" caption-side="bottom"}
=======
{: caption="List of DCs and their corresponding AT instance region" caption-side="bottom"}
>>>>>>> Stashed changes
