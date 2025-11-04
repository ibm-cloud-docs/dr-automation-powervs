---

copyright:
  years: 2025
lastupdated: "2025-11-04"

subcollection: dr-automation-powervs

keywords: known issues

---

# Known limitations
{: #knowlim}

IBM® strives to keep issues in {{site.data.keyword.DR_full}} to a minimum, but occasionally they can't be avoided. Learn about the known issues in this release. IBM is aware of these issues and is working hard to address them as quickly as possible.
{:shortdesc: .shortdesc}

## External orchestrator
{: #ext}

## July 2025
{: #jul-25}

1. DR Rehearsal does not support shared processor pool.
2. Rehearsal supports VMs with a maximum of 30 disks.
3. Unmanaging multiple VMs in parallel is not supported in the current release. Unmanaging  operations must be performed one VM at a time to avoid system crashes.

## December 2024
{: #dec-cem-24}

1. Ensure that no backup workspace VM with the same name, prefixed with `_BackUp`, exists during discovery when creating a fresh cluster. If such a VM exists, it will cause the discovery process to fail and may impact existing backup VMs.
2. If a VM is configured with a public IP in the PowerVS environment, and static IP settings are enabled at both the system and workspace levels from Orchestrator(KSYS), we will not retain the same IP settings after performing a planned or unplanned move operation on the target site.
3. Before unmanaging a disk in the KSYS environment, ensure the VM configuration is refreshed to include any newly added volumes. Run a discovery operation to update KSYS with the latest resource details linked to the VM. If discovery is not performed before unmanaging, the following error may occur:

  - Volume does not belong to the specified Workgroup. Query the resource class to view the configured resources.
    >**Note:** To avoid above error run command `ksysmgr refresh vm <vmname>`
