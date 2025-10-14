---

copyright:
  years: 2025
lastupdated: "2025-10-14"

subcollection: dr-automation

keywords: event-logs, ksys events, events 

---

# Orchestrator events
{: #orch-events}

The orchestrator continuously monitors and records events that occur during disaster recovery (DR) automation operations. These events provide information about key system activities such as discovery, deployment, network configuration, and replication monitoring. Reviewing the event notifications helps you track the progress of operations, identify potential issues, and ensure that the DR environment is functioning as expected.

You can use the ksysmgr query event command to view all recorded events or filter them by event type, such as error, warning, or info. Monitoring these events helps maintain visibility into orchestrator operations and supports proactive system management.


## Viewing orchestrator event logs
{: #view-orchestrator-event-logs}

The orchestrator tracks various events in the environment and saves the information in **log** files.

You can run the following command to list all the events that can be notified:

```shell
ksysmgr query event

```

To query all events of a specific event type, use the following command:

```shell
ksysmgr query event type=error|warning|info

```

The following table lists events that the orchestrator monitors:

## Orchestrator events
{: #notifiy-events}

The following table lists the events that can occur during external orchestrator operations. Each event includes its type and a brief description to help you identify the status or issues during execution.

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
{: caption="List of events" caption-side="bottom left"}

 >  **Note:**{: #note}
  >
  >- Users might not receive event notifications while disaster recovery operations are in progress, as the quick discovery process is blocked during these operations.
 >- The KSYS subsystem sends site event notifications without considering the value of the notification_level system attribute.
