---
front_matter_title: "KSYS events"
lastupdated: "2024-10-23"
copyright: "2023, 2024"
subcollection: dr-automation
---
# Notification for the KSYS Events

The KSYS subsystem tracks various events in the environment and saves the information in log files.

You can run the following command to list all the events that can be notified:

```shell
ksysmgr query event

```

To query all events of a specific event type, use the following command:

```shell
ksysmgr query event type=error|warning|info

```

The following table lists events that the KSYS monitors:

## Table 1: Notification for KSYS Events

| **Events**                     | **Event Type**   | **Description**                                |
|---------------------------------|------------------|------------------------------------------------|
| DISCOVERY_FAILED               | Critical         | Discovery has failed.                          |
| MIGRATED_VM_EXISTS_IN_WG       | Critical         | Migrated VM exists in workgroup.              |
| DEPLOY_FAILED                  | Critical         | Deploy VM has failed.                         |
| GRS_ENABLE_VOLUMES_FAILED      | Informational    | Volumes DR enablement has failed.             |
| ONBOARD_VOLUMES_FAILED         | Critical         | Volumes onboard has succeeded.                |
| ATTACH_VOLUMES_FAILED          | Critical         | Volumes attach has failed.                    |
| VM_SHUTDOWN_FAILED             | Critical         | VM shutdown has failed.                       |
| VM_BOOTUP_FAILED               | Critical         | VM bootup has failed.                         |
| REPLICATION_MONITOR_FAILED     | Critical         | Replication monitor has failed.               |
| MOVE_FAILED                    | Critical         | Move has failed.                              |
| VG_REVERSAL_FAILED             | Critical         | VG reversal has failed.                       |
| VG_STOP_FAILED                 | Critical         | VG stop has failed.                           |
| VG_UPDATE_FAILED               | Warning          | VG update has failed.                         |
| VG_REMOVE_FAILED               | Critical         | VG remove has failed.                         |
| VG_REMOVE_DISKS_FAILED         | Critical         | VG remove disks has failed.                   |
| VM_REMOVE_FAILED               | Warning          | VM remove has failed.                         |
| VM_MISSED_FROM_WORKSPACE_PHASE | Critical         | VM missed from the workspace.                 |
| SCRIPT_FAILURE_EVENT           | Critical         | Script execution has failed.                  |
{: caption="List of events" caption-side="bottom"}

 >Note:
 
 >Users might not receive event notifications while disaster recovery operations are in progress, as the quick discovery process is blocked during these operations.

 >The VM_CPU_THRESHOLD_EXCEEDED event can be ignored when VM uses shared processors in uncapped mode.

 >The KSYS subsystem sends site event notifications without considering the value of the notification_level system attribute.
