---
front_matter_title: "Limitations"
lastupdated: "2024-10-23"
copyright: "2023, 2024"
subcollection: dr-automation
---

# Limitations

## External orchestrator

1. Ensure backup workspace vm same name with prefix _BackUp is not existing during discovery on fresh cluster create. If, so discovery fails and might affect existing backup vm created.
2. If a VM is configured with a public IP in the PowerVS environment, and static IP settings are enabled at both the system and workspace levels from Orchestrator(KSYS), we will not retain the same IP settings after performing a planned or unplanned move operation on the target site.
3. Before unmanaging a disk in the KSYS environment, ensure the VM configuration is refreshed to include any newly added volumes. Run a discovery operation to update KSYS with the latest resource details linked to the VM. If discovery is not performed before unmanaging, the following error may occur:

    Volume does not belong to the specified Workgroup. Query the resource class to view the configured resources.

    >Note: To avoid above error run command `ksysmgr refresh vm <vmname>`
