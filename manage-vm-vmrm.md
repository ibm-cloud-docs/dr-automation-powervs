---

copyright:
  years: 2025
lastupdated: "2025-01-16"

subcollection: dr-automation

keywords: manage-ummanage

---

# Managing VM sessions
{: #manage-vm-ses}

Efficiently set up and manage VM sessions by creating new sessions, organizing virtual machines into WorkGroups, and saving configurations for streamlined virtual machine management.
{:shortdesc: .shortdesc}

## Create a new VM session
{: #create-vm-ses}

After creating the sites, you must create a new VM session if you are managing the virtual machine for the first time. If the virtual machine has already been managed, you can proceed directly to [manage the VM](#manage-vm) and [unmange VM](#unmanage-vm) the sessions.

To create and manage virtual machines, complete the following steps:

1. Click **Create New Session**.

2. To create WorkGroups, search for or select the virtual machines based on your requirements.

3. Display only the selected virtual machines for the session.

4. To create the Target Workspace, search for or select the virtual machines according to your requirements, and click **Save & Next**.

> **Note**: The WorkGroup name is auto-generated based on the VM name. You can modify it if necessary.

## Manage VM
{: #vm-ses}

You can view and manage VMs using the VM Recovery Manager DR (GUI). Managing a VM allows it to be included in disaster recovery operations and monitored effectively.

To manage the VMs, complete the following steps:

1. In the navigation pane of the VM Recovery Manager DR, click **Site > WorkSpace > Managed this VM**.
2. Select the VM.
3. Click **Manage this VM**.

   You are redirected to the Managed VM tab, where you can view details such as:
   - VM Name
   - WorkGroup
   - Source Workspace
   - Target Workspace

> **Note:** The WorkGroup name is auto-generated based on the VM name. You can change it as per your requirements.


## Unmanage VM
{: #um-manage-ses}

You can view and unmanage VMs using the VM Recovery Manager DR (GUI). Unmanaging a VM removes it from disaster recovery operations and monitoring.

To unmanage the VMs, complete the following steps:

1. In the navigation pane of the VM Recovery Manager DR, click **Site > WorkSpace > Unmanaged this VM**.
2. Select the VM.
3. Click **Unmanage this VM**.

   After this operation, the WorkGroup is removed from the list.

  >  **Note:**
   > - Each WorkGroup is associated with only one VM.  
   > - You can unmanage a VM even if it has not been managed previously.
