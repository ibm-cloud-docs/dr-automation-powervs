---

copyright:
  years: 2025
lastupdated: "2026-04-06"

subcollection: dr-automation-powervs

keywords: manage vm, modify vm, create vm, update vm, create virtual machine, add virtual machine, modify virtual machine

---

# Managing VM sessions
{: #manage-vm-ses}

Efficiently set up and manage virtual machine sessions by creating new sessions, and grouping virtual machines into workgroups and save configuration for streamlined virtual machine management.
{:shortdesc: .shortdesc}

## Create a new VM session
{: #create-vm-ses}

After adding the sites, you must create a new VM session if you are managing the virtual machine for the first time.

## Manage VM
{: #manage-vm-session}

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

> **Note**: If no values are specified for **Flex Capacity**, the **Target Flex Memory (%)** and **Target Flex CPU (%)** are set to 100% by default.

### Modify Dedicated Hostgroup and Dedicated Host

To configure dedicated hostgroup and dedicated host, complete the following steps:

1. In the **Modify VM** step, select the virtual machine.

2. Expand the **Dedicated Hostgroup** and **Dedicated Host** section.

3. Select the required dedicated hostgroup or dedicated host from the available list.

4. You can also click the expand icon to open the selection window, choose the appropriate **Dedicated Hostgroup** and **Dedicated Host**, and click **Submit**.

5. Click **Save & Next**.

6. Review the configuration in the **Summary** page and click **Submit & Deploy** to apply the changes.

## Network pairing
{: #network-pairing}

Network pairing establishes communication links between network devices or systems to ensure seamless data transmission and operational connectivity. This is an **optional setup** and is typically performed after managing virtual machines (VMs) and organizing them into WorkGroups. After completing the VM management process, the GUI navigates you to the **Network Pairing** page.
{:shortdesc: .shortdesc}

All VMs that are added to the WorkGroup are automatically populated on the **Network Pairing** page.

### Procedure
{: #network-proce}

To complete the network pairing, follow these steps:

1. Select the VM that requires network pairing from the list.
2. Select the source network from the **Source Network** drop-down menu and the corresponding target network from the **Target Network** drop-down menu, and you can now map multiple networks for each VM as part of the network selection process.
3. If you need to create a new target network, click **Create New Target Network** and configure the required settings.
4. Click **Save & Next** to finalize the network pairing.
5. To review the paired networks, click **Show Network Pairs**.
6. To clear the pairing, click **Clear Selection** and confirm to unpair the network configuration.

> **Note**: When confirming network pairings for one VM within a shared workspace and network setup, the confirmation is automatically applied to other VMs with similar configurations.

## IP mapping
{: #ip-mapping}


IP mapping allows you to define the mapping between source and target IP addresses for the selected virtual machines. This is an **optional setup** and is available only when Static IP is enabled during VM session creation. After completing the network pairing process, the GUI navigates you to the **IP Map** page.
{:shortdesc: .shortdesc}

All VMs that are added to the WorkGroup are automatically populated on the **IP Map** page.

### Procedure
{: #ip-mapping-procedure}

To configure IP mapping, follow these steps:

1. Select the VM that requires IP mapping from the list.

2. Verify that **Static IP Enable** is set to **Yes**.

3. In the **Static IP Map** section, enter the following details:
   - **Source IP Address**
   - **IP Address to Map**

4. Click **Add IP** to add the mapping.

5. You can add multiple IP mappings for each VM as part of the configuration.

6. Click **Save** to retain the IP mapping configuration.

7. To remove the mapping, use the available option to clear the selected entries.

> **Note**: If no IP mapping is configured, the default network configuration is applied.

## Summary
{: #summary}

The Summary page provides an overview of the configuration details for the selected virtual machines before deployment. This includes information such as VM name, source and target workspaces, workgroup, target VM details, configured IP mappings, and processor pool settings.
{:shortdesc: .shortdesc}

Review all the configured details carefully to ensure accuracy.

### Procedure
{: #summary-procedure}

To review and complete the configuration, follow these steps:

1. Verify the VM configuration details displayed in the **Configuration Summary** section.

2. Click **Export Summary** to download the configuration details, if required.

3. Click **Back** to modify any configuration settings.

4. Click **Submit & Deploy** to apply the configuration and initiate deployment.

The following details are displayed in the summary page:

- **VM Name**: The unique identifier assigned to each virtual machine for management and configuration purposes.  
- **Source Workspace**: The workspace from which the virtual machine originates.  
- **Target Workspace**: The workspace where the virtual machine is deployed or managed.  
- **Workgroup Name**: The name assigned to the group of virtual machines for collective management. 
- **Target System**: The network configuration to which the virtual machine is connected after pairing.
- **Static IP Map**: Displays the mapping between the source IP address and the target IP address, if static IP was enabled.  
- **Enable Shared Procpool**: Indicates whether virtual machines are configured to share processor capacity dynamically through a shared processor pool (SPP).
- **Target Procpool**: The designated shared processor pool (SPP) that is assigned to the virtual machines.
