---

copyright:
  years: 2025
lastupdated: "2025-01-31"

subcollection: dr-automation

keywords: network-pairing

---

# Creating network pairing (Optional)
{: #network-pairing}

Network pairing establishes communication links between network devices or systems to ensure seamless data transmission and operational connectivity. This is an **optional setup** and is typically performed after managing virtual machines (VMs) and organizing them into WorkGroups. After completing the VM management process, the GUI navigates you to the **Network Pairing** page.
{:shortdesc: .shortdesc}

All VMs that are added to the WorkGroup are automatically populated on the **Network Pairing** page.

## Procedure

To complete the network pairing, follow these steps:

1. Select the VM that requires network pairing from the list.
2. Select the source network from the **Source Network** drop-down menu and the corresponding target network from the **Target Network** drop-down menu.
3. If you need to create a new target network, click **Create New Target Network** and configure the required settings.
4. Click **Save & Next** to finalize the network pairing.
5. To review the paired networks, click **Show Network Pairs**.
6. To clear the pairing, click **Clear Selection** and confirm to unpair the network configuration.

> **Note**: When confirming network pairings for one VM within a shared workspace and network setup, the confirmation is automatically applied to other VMs with similar configurations.

## Network details on dashboard
{: #network-details}

To view the network details, follow these steps:

1. Select the workspace to view network details.
2. Click **Network Information** on the main screen to see the associated networks.
3. Click **View Networks** next to the desired workspace for detailed network data.

You can see the following details about the selected network:

- **Network Name:** The name that is assigned to the network.
- **VM Name:** Lists the names of the virtual machines that are connected to the network.
- **Network ID:** A unique identifier for the network.
- **Subnet Range:** Specifies the range of IP addresses within the subnet.
- **Gateway:** Displays the gateway IP address.
- **VLAN ID:** Shows the VLAN ID associated with the network.
