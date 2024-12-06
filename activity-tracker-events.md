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

## 1. Instance events

Instance events are essential for assessing the status and readiness of instances for failover within {{site.data.keyword.DR_short}}. These events allow administrators to list and monitor instances to ensure they are prepared for rapid recovery during a disaster scenario.

| **Action**                | **Description**                                       |
|---------------------------|-------------------------------------------------------|
| `dr-instance.list`        | Lists all instances that are configured for failover. |
| `dr-instance.read`        | Reads the status of a specified instance for readiness verification. |
{: caption="List of events: Instance" caption-side="bottom"}

### Example use case

In preparation for disaster recovery testing, an administrator may use `dr-instance.list` to retrieve all instances under {{site.data.keyword.DR_short}}. By reading the status of each instance, they ensure that all critical systems are in a ready state for immediate failover.

---

## 2. Images events

Image events support the creation and management of system images necessary for backup and recovery. This is crucial in DR scenarios, where the availability of up-to-date images allows for rapid restoration of workloads.

| **Action**                | **Description**                                |
|---------------------------|------------------------------------------------|
| `dr-image.create`         | Creates a new image of a configured instance.  |
| `dr-image.list`           | Lists all images available for recovery.       |
| `dr-image.delete`         | Deletes an outdated image to manage storage.   |
{: caption="List of events: Images" caption-side="bottom"}

**Example use case**
During the setup of {{site.data.keyword.DR_short}}, an administrator may use `dr-image.create` to capture a backup image of an instance. This image can then be listed and validated to ensure it is available for future recovery operations.

---

## 3. Network events

Network events are critical for configuring and managing network paths that facilitate connectivity between primary and backup sites, ensuring uninterrupted communication during a DR event.

| **Action**                | **Description**                                               |
|---------------------------|---------------------------------------------------------------|
| `dr-network.list`         | Lists all network paths configured for DR operations.         |
| `dr-network.create`       | Establishes a network path essential for failover.            |
| `dr-network.update`       | Updates the configuration of an existing DR network path.     |
{: caption="List of events: Network" caption-side="bottom"}

**Example use case**
To prepare for a potential failover, an administrator can use `dr-network.list` to confirm that network paths are active. If additional configuration is needed, `dr-network.create` can establish the required connectivity.

---

## 4. Power virtual server events

For {{site.data.keyword.DR_short}}, these events provide control over virtual server instances, allowing administrators to start, stop, or capture snapshots for recovery purposes.

| **Action**                         | **Description**                                       |
|------------------------------------|-------------------------------------------------------|
| `dr-instance.start`                | Starts a virtual server instance for failover.        |
| `dr-instance.stop`                 | Stops an instance that is no longer required.         |
| `dr-instance.snapshot`             | Captures a snapshot of an instance for backup.        |
{: caption="List of events: Power Virtual Server" caption-side="bottom"}

**Example use case**
During a failover drill, an administrator can issue `dr-instance.start` to activate all necessary instances in the backup environment. Additionally, `dr-instance.snapshot` can be used to capture a real-time backup.

---

## 5. Data volumes events

Managing data volumes ensures that critical storage resources are available and can be quickly attached or detached as needed during failover operations.

| **Action**                | **Description**                                           |
|---------------------------|-----------------------------------------------------------|
| `dr-volume.create`        | Creates a new data volume for DR purposes.                |
| `dr-volume.attach`        | Attaches a data volume to an instance in the backup site. |
| `dr-volume.detach`        | Detaches a data volume after a failover test.             |
{: caption="List of events: Data Volume Events" caption-side="bottom"}

**Example use case**
In the event of a failover, an administrator may use `dr-volume.attach` to ensure that critical storage volumes are available to the restored instances at the backup site.

---

## 6. Cloud connections events

Cloud connection events facilitate secure connectivity between the primary and backup environments, which is crucial for data replication and failover communication.

| **Action**                | **Description**                                                   |
|---------------------------|-------------------------------------------------------------------|
| `dr-cloud-connection.list`| Lists all cloud connections between primary and backup sites.     |
| `dr-cloud-connection.create`| Establishes a secure connection between DR sites.               |
| `dr-cloud-connection.update`| Updates the configuration of an existing cloud connection.     |
{: caption="List of events: Cloud Connections" caption-side="bottom"}

**Example use case**
To ensure continuity during a failover, an administrator uses `dr-cloud-connection.list` to verify all connections between the primary and backup sites are active. If needed, `dr-cloud-connection.update` can modify the connection parameters.

---

## 7. Security related events

Security-related events are critical to maintaining secure connections during a DR failover, particularly through VPN, IKE, and IPsec configurations.

| **Action**                          | **Description**                                      |
|-------------------------------------|------------------------------------------------------|
| `dr-vpn.list`                       | Lists all VPN configurations for secure DR paths.    |
| `dr-ike-policy.create`              | Creates an IKE policy to secure DR data transfer.    |
| `dr-ipsec-policy.update`            | Updates an IPsec policy for secure site connectivity.|
{: caption="List of events: Security-Related" caption-side="bottom"}

**Example use case**
For secure data transfer, an administrator can use `dr-vpn.list` to confirm active VPN connections. To enhance security, `dr-ike-policy.create` and `dr-ipsec-policy.update` can be applied as required.

---

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
{: caption="List of DCs and their corresponding AT instance region" caption-side="bottom"}
