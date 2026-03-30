---

copyright:
  years: 2025
lastupdated: "2026-03-30"

subcollection: dr-automation-powervs

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

4. Select the **Target Workspace** from the available list, and click **Save & Next**.  

## Modify VM
{: #modify-vm-ses}

Make changes to your virtual machines as needed. In this step, select the virtual machines to update and configure target environment settings by using the available sections: Modify VM to configure basic settings such as IP mapping and Shared Processor Pool (SPP), Flex Capacity to control CPU and memory allocation for inactive and failover states, Dedicated Hostgroup to specify hostgroup-level placement, and Dedicated Host to specify host-level placement for isolation and predictable resource allocation.

### Modify VM 
{: #mod-vm-ses}

To modify virtual machine, complete the following steps:

1. All virtual machines are displayed. Select the virtual machines to enable the **Shared Procpool** option.  

2. If you have selected **Yes** to enable Static IP while [creating a new VM session](#create-vm-ses), enter the **Target IP Address details** that are **Source IP Address** and **IP Address to Map**.

   > **Note:** You can add multiple IP mappings.

3. Select **Yes** and enter the **Target Procpool** details to enable the **shared processor pool (SPP)**, that allows VMs to share processor capacity dynamically. Select **No** to skip this option.  
4. Click **Save & Next**.

> **Note:** Click **Refresh VM List** to display all available VMs.

### Modify Flex Capacity
{: #mod-fl-capacity}

To configure Flex capacity, complete the following steps:

1. In the **Modify VM** page, select the virtual machine.

2. Expand the **Flex Capacity** section.

3. Provide the required values:
   - **Target Flex Memory (%)**: Percentage of total memory allocated during failover.
   - **Target Flex CPU (%)**: Percentage of CPU allocated during failover.
   - **Inactive VM Memory**: Minimum memory when the VM is inactive. Specify an integer value with a minimum of 2 GB.
   - **Inactive VM CPU**: Minimum CPU when the VM is inactive. Specify a value in multiples of 0.25 cores.

4. Click **Save & Next**.

5. Review the configuration in the **Summary** page and click **Submit & Deploy** to apply the changes.
6. In the dashboard page, select the VM. The **Summary** and **Flex Capacity** tabs are displayed. Click **Flex Capacity** to review and modify **Target Flex Memory (%)**, **Target Flex CPU (%)**, **Inactive VM Memory**, and **Inactive VM CPU** as required.

> **Note**: If no values are specified for **Flex Capacity**, the **Target Flex Memory (%)** and **Target Flex CPU (%)** are set to 50% by default.

### Modify Dedicated Hostgroup and Dedicated Host

To configure dedicated hostgroup and dedicated host, complete the following steps:

1. In the **Modify VM** step, select the virtual machine.

2. Expand the **Dedicated Hostgroup** and **Dedicated Host** section.

3. Select the required dedicated hostgroup or dedicated host from the available list.

4. You can also click the expand icon to open the selection window, choose the appropriate **Dedicated Hostgroup** and **Dedicated Host**, and click **Submit**.

5. Click **Save & Next**.

6. Review the configuration in the **Summary** page and click **Submit & Deploy** to apply the changes.


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
