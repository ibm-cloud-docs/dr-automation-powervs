---

copyright:
  years: 2025
lastupdated: "2025-07-16"

subcollection: dr-automation

keywords: event-logs

---

# Managing events logs
{: #manage-log}

The **Events** tab in the {{site.data.keyword.DR_full}} interface provides an overview of the key activities and status changes within your virtual server instances. This log of events enables administrators to track and review significant actions, such as server stops, starts, and any alerts or warnings that might require attention. Monitoring these events ensures that the disaster recovery environment functions optimally and that any potential issues can be promptly addressed.
{:shortdesc: .shortdesc}

## Accessing the event logs
{: #access-log}

You can access a maximum of 100 events for the current and previous months in the IBM Cloud console. To see the event logs, complete the following steps:

1. Log in to the [IBM Cloud catalog](https://cloud.ibm.com/catalog) with your credentials.
2. In the catalog's **search box**, type {{site.data.keyword.DR_full}}, and click the Workspace for {{site.data.keyword.DR_full_notm}} tile.
3. Select **workspace** on the left navigation under workspace of the {{site.data.keyword.DR_full}} user  interface to select from a list of previously created workspaces. If you do not have a workspace, click Create a workspace.
4. Click **Event logs** to see the list of event logs and notifications.

## Administrating event logs
{: #adm-log}

Administrators can view detailed records of the virtual server activities, including:

- The kind of event that occurred, such as actions on virtual server instances.

- A description of the event, for example, whether the virtual server was stopped or any other relevant action was taken.

- The exact time and date the event was logged, helping track the sequence of activities.

- The importance level of the event, which could range from informative (Info) to critical warnings (Caution).

## Notification for the KSYS events

The KSYS subsystem tracks various events in the environment and saves the information in **log** files.

You can run the following command to list all the events that can be notified:

```shell
ksysmgr query event

```

To query all events of a specific event type, use the following command:

```shell
ksysmgr query event type=error|warning|info

```

The following table lists events that the KSYS monitors:

## Notification for KSYS events
{: #notifiy-events}


| **Events**                     | **Event Type**    | **Description**                           |
|--------------------------------|-------------------|-------------------------------------------|
| DISCOVERY_FAILED               | Critical          | Discovery has failed.                     |
| DISCOVERY_COMPLETED            | Informational     | Discovery process has completed.          |
| AUTO_DISCOVERY_STARTED         | Informational     | Auto discovery process has started.       |
| AUTO_DISCOVERY_SUCCESS         | Informational     | Auto discovery process completed.         |
| AUTO_DISCOVERY_FAILED          | Critical          | Auto discovery process has failed.        |
| NETWORK_CONFIGURATION_STARTED  | Informational     | Network configuration process has started.|
| NETWORK_CONFIGURATION_SUCCESS  | Informational     | Network configuration process completed.  |
| NETWORK_CONFIGURATION_FAILED   | Warning           | Network configuration process has failed. |
| DEPLOY_FAILED                  | Critical          | Deploy VM has failed.                     |
| GRS_ENABLE_VOLUMES_FAILED      | Informational     | Volumes DR enablement has failed.         |
| ONBOARD_VOLUMES_FAILED         | Critical          | Volumes onboard has succeeded.            |
| ATTACH_VOLUMES_FAILED          | Critical          | Volumes attach has failed.                |
| VM_SHUTDOWN_FAILED             | Critical          | VM shutdown has failed.                   |
| VM_BOOTUP_FAILED               | Critical          | VM bootup has failed.                     |
| REPLICATION_MONITOR_FAILED     | Critical          | Replication monitor has failed.           |
| MOVE_FAILED                    | Critical          | Move has failed.                          |
| VG_REVERSAL_FAILED             | Critical          | VG reversal has failed.                   |
| VG_STOP_FAILED                 | Critical          | VG stop has failed.                       |
| VG_UPDATE_FAILED               | Critical          | VG update has failed.                     |
| VG_REMOVE_FAILED               | Critical          | VG remove has failed.                     |
| VG_REMOVE_DISKS_FAILED         | Critical          | VG remove disks has failed.               |
| VM_MISSED_FROM_WORKSPACE_PHASE | Critical          | VM missed from the workspace.             |
| SCRIPT_FAILURE_EVENT           | Critical          | Script execution has failed.              |
{: caption="List of events" caption-side="bottom"}

 >  **Note:**{: #note}
  >
  >- Users might not receive event notifications while disaster recovery operations are in progress, as the quick discovery process is blocked during these operations.
 >- The KSYS subsystem sends site event notifications without considering the value of the notification_level system attribute.
