---
front_matter_title: "Nav"
lastupdated: "2024-10-23"
copyright: "2023, 2024"
subcollection: dr-automation
---

# Navigation Panel

On the left of the dashboard, the navigation panel displays KSYS clusters, sites, workspaces, and site-specific details. This panel also provides the **overall count** of associated workspaces, workgroups, and unmanaged VMs, offering a quick overview of available resources.

1. **KSYS Cluster Navigation**:
   - Displays the KSYS cluster type, cluster name (e.g., `ksysclusterTest`), and the overall count of associated workspaces.
   - Expand this section to view specific details and take actions related to the cluster.

2. **Site Navigation (e.g., Site-2)**:
   - Lists regions (e.g., USA, India) with their respective overall counts of associated workspaces, workgroups, and unmanaged VMs.
   - Expand a site to explore specific resources.

3. **Workspace Navigation**:
   - Displays the workspace details along with the overall count of associated workgroups and unmanaged VMs for the selected workspace.
   - For example, you can view the count for `VMRM-wdc` and `VMRM-TEST-DAL10`.

4. **Unmanaged VMs and Workgroups**:
   - Provides the total count of unmanaged VMs and Workgroups that are not yet managed by the system.
   - Expand these sections to perform actions like managing the VMs or viewing additional details.

**Tip:** Use the search box at the bottom of the navigation panel to quickly locate specific VMs or Workgroups.

## Summary

To access the Summary tab and view ongoing issues, follow these steps:

1. Select the cluster (e.g., `ksysclusterTest`) from the navigation panel.
2. Click on **Summary** in the top navigation bar.
3. View critical events, warnings, and configuration status of Workgroups and unmanaged VMs.

**Features:**

- **Critical Events**: Displays a count of critical events. Hover over the count to view detailed issues.
- **Warnings**: Highlights potential problems requiring attention.
- **Configuration Status**: Indicates the health of Workgroups and unmanaged VMs.

---

## Events

To analyze detailed information about events in your environment:

1. Select the cluster from the navigation panel.
2. Click on **Summary** in the top navigation bar.
3. Navigate to the **Events** tab by clicking on the Events option.

**Features:**

- **Event Details**: Shows the time of occurrence, a description, and the severity of each event.
- **Filter Events**: Use filters to display specific event types, such as critical events or warnings.
- **View Details**: Click on an event to view its full details, including potential resolutions.

---

## Tunable Policies

To view and update system tunable attributes in the **Policies** tab:

1. Select the cluster from the navigation panel.
2. Click on **Policies** in the top navigation bar.
3. Navigate to the **Policies** tab.
4. Edit the fields such as Auto Discovery Time, Notification Level, and Trace File Size as required.
5. Click **Save & Update** to apply changes.

### Policies

- **Auto Discovery Time**: Configures the frequency (in hours) for the system to automatically discover new resources in the cluster.
- **Duplicate Event Processing**: Indicates whether duplicate events should be processed (Yes/No).
- **Quick Discovery Interval**: Specifies the interval (in minutes) for quick scans of cluster resources to detect any changes.
- **Trace File Size**: Sets the maximum allowable size (in MB) for trace files generated during system operations.
- **Deep Discovery**: Enables or disables a comprehensive scan of cluster resources for detailed insights.
- **KSYS Spooling**: Allows configuration of the spooling path for KSYS logs or system outputs.
- **API Key**: Displays or configures the API key used for secure authentication with the DR system.
- **KSYS Language**: Specifies the language used for KSYS operations and system notifications.
- **Notification Level**: Sets the severity level of notifications issued by the system (Low, Medium, or High).
- **Custom Script Timeout**: Configures the timeout duration (in seconds) for executing custom scripts during operations.
- **Quick Discovery**: Toggles the quick discovery process to monitor resource updates more frequently.
- **Cleanup Files Interval**: Defines the time interval (in days) for cleaning up temporary or obsolete files in the system.

## Disk Mapping

The Disk Mapping feature is applicable at the Workgroup level and provides a detailed view of disk configurations between the source and target sites. It allows users to understand the mapping of disks and their relationships in disaster recovery operations.

### Key Details

1. **Source and Target Sites**: Displays disk mapping information for both the source and target sites.
2. **Consistency Group and Volume Group**: For each site, the associated **Consistency Group** name and **Volume Group** name are shown, enabling better tracking and management.
3. **Source Site Information**:
   - **Disk ID**: Lists the disk identifiers for the source site.
   - **Active VM**: Displays the name of the VM currently active at the source site.
4. **Target Site Information**:
   - **Disk ID**: Lists the disk identifiers for the target site.
   - **Partner VM**: Displays the name of the partner (backup) VM at the target site.

### Steps to Access Disk Mapping

1. Select the desired Workgroup from the navigation panel.
2. Click on the **Disk Mapping** tab in the main interface.
3. Review the displayed mapping between the source and target sites, including disk details, Consistency Groups, and Volume Groups.

## User Scripts Tab

To manage custom scripts for automating processes in the DR environment:

1. Select the cluster from the navigation panel.
2. Click on **User Scripts** in the top navigation bar.
3. Navigate to the **User Scripts** tab.
4. Edit the paths for scripts such as Before Shutdown, After Online, or Before Network Configuration.
5. Save your changes to apply the modifications.

## KSYS Details

To manage nodes in the KSYS cluster:

1. Select the cluster from the navigation panel.
2. Click on **KSYS Details** in the top navigation bar.
3. Perform the desired action:
   - **Adding a Node**: Click **Add Node**, enter the node details, and click **Add**.
   - **Deleting a Node**: Select the node, click **Delete Node**, and confirm the deletion.
   - **Registering a Node**: Click the **Register** button next to an unregistered node, add the required details, and click **Register**.
   - **Unregistering a Node**: Click the **Unregister** button next to the node.

## KSYS Settings Tab

To manage KSYS settings:

1. Select the cluster from the navigation panel.
2. Click on **KSYS Details** in the top navigation bar.
3. Click **Settings** in the top right corner.
4. Choose one of the available actions:
   - Unregister KSYS
   - Remove KSYS Cluster
   - Update Notification Preferences

## Inventory Tab

The Inventory tab provides a detailed overview of the resources attached to the KSYS cluster, segmented by sites (e.g., USA, DAL). It is used to monitor and manage the resources associated with each site, such as system types, managed VMs, and cores.

This information allows users to track resource utilization efficiently across sites and system types.

Following are the details:

1. **Site-Specific Inventory**:
   - Displays information for each site separately (e.g., USA, DAL).
   - Each site is categorized by system type (e.g., `s922`).

2. **Managed VMs**:
   - Shows the total number of managed VMs for each system type in the site.

3. **Managed Cores**:
   - Displays the total number of managed cores for each system type.

4. **Consolidated View**:
   - Provides a total count of managed VMs and cores for all system types within a site.

### Steps to Access Inventory

1. Select the desired **KSYS Cluster** from the navigation panel.
2. Click on **Inventory** in the top navigation bar.
3. View the site-specific inventory details:
   - Identify the **System Type** for each site (e.g., `s922`).
   - Review the **Number of Managed VMs** and **Number of Managed Cores** for each system type.
   - Check the **Total** row for a consolidated count of managed resources in the site.

### Example

- **Site: USA**
  - **System Type**: `s922`
  - **Number of Managed VMs**: 2
  - **Number of Managed Cores**: 2
  - **Total**: 2 Managed VMs and 2 Managed Cores

- **Site: DAL**
  - **System Type**: `s922`
  - **Number of Managed VMs**: 2
  - **Number of Managed Cores**: 3
  - **Total**: 2 Managed VMs and 3 Managed Cores

## Workgroup Active and Partner VMs

To view details about Active and Partner VMs for a Workgroup:

1. Expand the Workgroup from the navigation panel.
2. View the details under the Workgroup Summary section.
3. Check for the **Active VM** (currently running VM) and **Partner VM** (backup VM for failover).

---
