---

copyright:
  years: 2025
lastupdated: "2025-02-26"

subcollection: dr-automation

keywords: manage-ummanage

---

# Managing VM sessions
{: #manage-vm-ses}

Efficiently set up and manage VM sessions by creating new sessions, organizing virtual machines into workgroups, and saving configurations for streamlined virtual machine management.
{:shortdesc: .shortdesc}

## Create a new VM session
{: #create-vm-ses}

After creating the sites, you must create a new VM session if you are managing the virtual machine for the first time. If the virtual machine is already managed, you can proceed directly to [manage the VM](#vm-ses) and [unmanage VM](#um-manage-ses) sessions.

To create and manage virtual machines, complete the following steps:

1. Click **Create New Session**.

2. To create workgroups, search for or select the virtual machines that are based on your requirements.

3. Display only the selected virtual machines for the session.

4. To create the target workspace, search for or select the virtual machines according to your requirements, and click **Save & Next**.

> **Note**: The workgroup name is auto-generated and is based on the VM name. You can modify it if necessary.

## Manage VM
{: #vm-ses}

You can view and manage VMs by using the VM Recovery Manager DR (GUI). Managing a VM allows be included in disaster recovery operations and monitored effectively.

To manage the VMs, complete the following steps:

1. In the navigation page of the VM Recovery Manager DR, click **Site > workspace > Managed this VM**.
2. Select the VM.
3. Click **Manage this VM**.
4. You are redirected to the Managed VM tab, where you can view the following details:
   - VM Name
   - Workgroup
   - Source workspace
   - Target workspace


## Unmanage VM
{: #um-manage-ses}

You can view and unmanage VMs by using the VM Recovery Manager DR (GUI). Unmanaging a VM removes the VM from disaster recovery operations and monitoring.

To unmanage VMs, complete the following steps:

1. In the navigation page of the VM Recovery Manager DR, click **Site > workspace > Unmanaged this VM**.
2. Select the VM.
3. Click **Unmanage this VM**.
4. After this operation, the workgroup is removed from the list.

  >  **Note:**
   > - Each workgroup is associated with only one VM.  
   > - You can unmanage a VM even if it not managed previously.
