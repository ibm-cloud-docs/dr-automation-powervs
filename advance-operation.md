---
copyright:
  years: 2025
lastupdated: "2025-06-19"

subcollection: dr-automation-powervs

keywords: advance operation, advance, operation

---

# Advance operations
{: #ad-vance-load}

Advanced operations in the {{site.data.keyword.DR_full}} provide essential actions to manage and test your disaster recovery setup. This feature includes options such as **Failover Rehearsal**, **Clean up**, and **Re-Sync**. These actions help validate DR readiness, clear temporary artifacts, and maintain synchronization between sites

## Navigate advance operations
{: #na-vi-gate}

Follow these steps to access Advanced Operations for a selected workgroup in the {{site.data.keyword.DR_full_notm}} Ui:

1. **Select** the workspace from the navigation window.

2. **Expand** the workgroup list and select the **WorkGroup**.

3. Click the **Summary** tab and it displays **Advanced Operations**.

Click the Advanced Operations dropdown to choose from available actions such as **Failover Rehearsal**, **Clean up**, or **Re-Sync** to manage and test your disaster recovery setup.

## Failover rehearsal
{: #Fa-il-over}

**Failover Rehearsal** is a disaster recovery (DR) testing feature available at both the **site** and **workgroup** levels in Power Virtual Server DR Automation. It simulate a failover without affecting production by creating a temporary **Rehearsal VM** at the backup site. It helps validate your DR configuration is working as expected.

> **Important**: To initiate a rehearsal, discovery must be completed at the site or workgroup level.

### Procedure
{: #pro-ci-dure}

Follow these steps to perform the Failover Rehearsal:

1. **Select** the workspace and target **WorkGroup** from the navigation window.  
2. **Click** the **Advanced Operations** dropdown and **select** **Failover Rehearsal**.  
3. When prompted with a confirmation dialog, **click Yes** to proceed.  
4. **Monitor** the progress in the **Activity Log**.  
5. **Verify** that the **Rehearsal VM** appears under the **backup site**.  

This process helps ensure that disaster recovery operations can be validated without impacting the production environment.

## Cleanup
{: #cl-ea-nup}

The **Clean up** operation removes the Rehearsal VM created during a Failover Rehearsal. This helps restore the environment to its original state and ensures that no temporary resources remain after testing.

### Procedure
{: #cl-ea-pro}

Follow these steps to remove the Rehearsal VM created during a Failover Rehearsal:

1. **Select** the same **WorkGroup** used for rehearsal.  
2. **Click** the **Advanced Operations** dropdown and **select** **Clean up**.  
3. **Confirm** the operation when prompted.

Use this step after completing validation to maintain a clean and consistent DR setup.

## Re-sync a workgroup
{: #re-sy-nc}

The **Re-Sync** operation is used to synchronize the state of virtual machines in a workgroup between the active and backup sites. It helps ensure that the backup VM is updated with the latest configuration and data from the active VM. You can perform a resync to shut down the backup VM, synchronizes the state, and brings it back in sync with the active site. This operation is useful after configuration changes, DR tests, or failover rehearsals to maintain consistency across both sites.

### Procedure
{: #re-cy-cv}

Follow these steps to re-sync a workgroup in Power Virtual Server DR Automation:

1. **Select** the workspace and target **WorkGroup** from the navigation window.
2. **Click** the **Advanced Operations** dropdown.  
3. **Select** **Re-Sync** from the list of options.  
4. **Confirm** the operation when prompted.

The Re-Sync operation shuts down the backup VM, synchronize it with the active VM, and update its state to reflect the current production environment.
