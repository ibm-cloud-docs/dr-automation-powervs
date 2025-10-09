---

copyright:
  years: 2025
lastupdated: "2025-10-09"

subcollection: dr-automation

keywords: manage vm, modify vm, create vm, update vm, create virtual machine, add virtual machine, modify virtual machine

---

# Managing VM sessions
{: #manage-vm-ses}

Efficiently set up and manage virtual machine sessions by creating new sessions, and grouping virtual machines into workgroups and save configuration for streamlined virtual machine management.
{:shortdesc: .shortdesc}

## Create a new VM session
{: #create-vm-ses}

After adding the sites, you must create a new VM session if you are managing the virtual machine for the first time. If the virtual machine is already managed, you can proceed directly to [manage VM](#vm-ses) and [unmanage VM](#um-manage-ses) sessions.

### Procedure
{: #new-vm-ses}

To create and manage virtual machine, complete the following steps:

1. Click **Create New Session**.  

2. Select **Yes** to enable Static IP for all VMs, or select **No** to skip this option.  

3. To add a workgroup, search for or select the virtual machine as required.  

4. Provide the machine type in the **Target System** section, select the **Target Workspace** from the available list, and click **Save & Next**.  

## Modify VM
{: #modify-vm-ses}

The Modify VM option allows you to make changes to your virtual machines as needed. You can choose the VMs you want to update, adjust the IP mapping, and decide whether to enable the Shared Processor Pool (SPP) for improved performance and flexibility.

### Procedure
{: #mod-vm-ses}

To modify virtual machine, complete the following steps:

1. All virtual machines are displayed. Select the virtual machines to enable the **Shared Procpool** option.  

2. If you have selected **Yes** to enable Static IP while [creating a new VM session](#create-a-new-vm-session), enter the **Target IP Address details** that are Source IP Address and IP Address to Map.

   > **Note:** We can add mulitple IP mapping in this step.

3. Select **Yes** and enter the **Target Procpool** details to enable the **shared processor pool (SPP)**, which allows VMs to share processor capacity dynamically. Select **No** to skip this option.  
4. Click **Save & Next**.

> **Note:** Click **Refresh VM List** to display all available VMs.


## Manage VM
{: #vm-ses}

You can view and manage virtual machines by using the Power Virtual Server DR Automation UI. Managing a virtual machine and monitor effectively.

### Procedure
{: #ma-vm-se}

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

## Unmanage VM
{: #um-manage-ses}

You can view and virtual machines by using the Power Virtual Server DR Automation UI. Unmanaging a virtual machine removes the virtual machine from disaster recovery operations and monitoring.

### Procedure
{: #un-vm-manage}

To unmanage virtual machines, complete the following steps:

1. In the navigation page of the Power Virtual Server DR Automation, click **Site > Workspace > Worksgroup>Managed VM**.
2. Select the VM.
3. Click **Unmanage this VM**.
4. After this operation, the workgroup is removed and virtual machine is deleted.

   > **Note:**
   >
   > - Each workgroup is associated with only one virtual machine.
   > - You can unmanage a virtual machine even if it not managed previously.
