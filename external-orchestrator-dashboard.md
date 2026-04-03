---

copyright:
  years: 2025
lastupdated: "2026-04-03"

subcollection: dr-automation-powervs

keywords: manage vm, modify vm, create vm, update vm, create virtual machine, add virtual machine, modify virtual machine
---

# Dashboard View
{: #dashboard-view}


## Manage VM in dashboard
{: #vm-ses-dashboard}

You can view and manage virtual machines by using the Power Virtual Server DR Automation UI. Managing a virtual machine and monitor effectively.

### Procedure
{: #ma-vm-se-das}

To manage the additonal new virtual machines, complete the following steps:

1. In the Power Virtual Server DR Automation navigation page, click **Cluster Name > Site > Workgroup > Managed VM**.
2. Select the unmanged VM.
3. Click **Manage VM**.
4. You are redirected to the Managed VM tab, where you can view the following details:
   - VM Name
   - Workgroup
   - Source workspace
   - Target workspace
5. Complete the deployment flow to manage selected VM.

## Unmanage VM in dashboard
{: #um-manage-ses-dashboard}

You can view and virtual machines by using the Power Virtual Server DR Automation UI. Unmanaging a virtual machine removes the virtual machine from disaster recovery operations and monitoring.

### Procedure
{: #un-vm-manage-das}

To unmanage virtual machines, complete the following steps:

1. In the navigation page of the Power Virtual Server DR Automation, click **Site > Workspace > Worksgroup>Managed VM**.
2. Select the VM.
3. Click **Unmanage this VM**.
4. After this operation, the workgroup is removed and virtual machine is deleted.

   > **Note:**
   >
   > - Each workgroup is associated with only one virtual machine.
   > - You can unmanage a virtual machine even if it not managed previously.
