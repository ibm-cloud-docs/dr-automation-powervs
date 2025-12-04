---

copyright:
  years: 2025
lastupdated: "2025-12-04"

subcollection: dr-automation-powervs

keywords: getting started

---

# Managing events logs
{: #manage-log}

The **Events** tab in the {{site.data.keyword.DR_full}} interface provides an overview of the key activities and status changes within your virtual server instances. This log of events enables administrators to track and review significant actions, such as server stops, starts, and any alerts or warnings that might require attention. Monitoring these events ensures that the disaster recovery environment functions optimally and that any potential issues can be promptly addressed.
{:shortdesc: .shortdesc}

## Administrating event logs
{: #adm-log}

Administrators can view detailed records of the following Orchestrator VM activities:

- You can access up to 100 current events in the IBM Cloud console.
- DR automation displays pop-up notifications to keep you informed about important events, such as deployment status, errors, or other operational updates, with timestamps.
- Each notification is available only for 10 seconds.
- Events Table display the list of events generated for the DR Automation service with Headers like ResourceType, Action, Date, and Severity.
- You can sort Events based on your requirement by using the sort functionality on each Header.
- The search option is available to search for the required event.
- You can filter the events based on Resources, Levels and Actions.
- A detailed description is displayed for each event when you expand the event.
- The exact time and date when the event is logged help track the sequence of activities.
- The importance level of the event can range from informational (Info) to critical (Caution).

## DR Automation events
{: #dr-auto--eve-log}

The following table lists key events generated during various DR Automation operations, along with their corresponding actions and descriptions.

| **Events**                  | **Event Action** | **Description**                                  |
|-----------------------------|------------------|--------------------------------------------------|
| Provision ID                | Create           | Service provisioned successfully.                |
| Manage DR                   | Create           | Service has deployed.                            |
| Image                       | Download         | Image download has happened.                     |
| Virtual server instance      | Create           | Virtual server instance creation has started.    |
| Orchestrator                | Create           | Orchestrator cluster creation has started.       |
| Orchestrator                | Update           | Ksys running fine event has generated.           |
| API key                     | Update           | API key updation has happened.                   |
| Provision ID                | Delete           | Service has deleted.                             |
| MFA                | Create           | MFA registration for the instance has completed successfully for the tenant.                             |
{: caption="List of DR Automation events" caption-side="bottom"}

## Accessing the event logs
{: #access-log}

 To see the event logs, complete the following steps:

1. Log in to the [IBM Cloud catalog](https://cloud.ibm.com/catalog) with your credentials.
2. In the catalog's **search box**, type {{site.data.keyword.DR_full}}, and click the tile to provision the service and deploy the orchestrator to view the live events.
3. To view existing service events, click **Navigation Menu** > **Resource List** > **Compute**, then click on the provisioned instance you want to view and navigate to the Events table.
4. The Event logs section appears at the bottom of the page, displaying system events and notifications.
