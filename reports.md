---
copyright:
  years: 2025
lastupdated: "2025-12-04"

subcollection: dr-automation-powervs

keywords: reports, migration report, discover report, 

---
# Generate external orchestrator reports
{: #reports}

The Reports page in {{site.data.keyword.DR_full_notm}} provides a consolidated view of operational activities performed across sites and workspaces, enabling administrators to review historical events, track execution status, analyze execution time, and download report summaries for auditing or troubleshooting, including reports for **Discovery**, **Move**, **Failover Rehearsal**, and **Cleanup**.

## Discovery
{: #discovery-report}

The **Discovery** report provides information about discovery operations performed on a site or workspace, helping you track discovery activity, review failure reasons, and validate the overall discovery duration.

> **Note**: To generate a Discovery report, you must first run a discovery operation by clicking the **Discover Site** button from the site dashboard. Only after the discovery is completed is the report available to generate.

The report displays the following information:

- The discovery type shown in the **Discover on** field identifies the site or workspace on which the discovery was performed.
- The outcome of the discovery operation displayed in the **Status** field indicates whether the discovery completed successfully or failed.
- The duration of the discovery process shown in the **Approximate Time Taken** field provides the total time required to complete the discovery.
- The **Start Date** and **End Date** fields record when the discovery operation began and when it finished.
- The bar chart in the Discovery report visualizes the time taken for each discovery operation to help compare performance across executions.
- The summary panel containing **Total Discovery Count**, **Successfully Completed**, **Failed**, and **Average time taken** provides an overview of discovery events during the selected period.
- The **Export Summary** button enables you to download the discovery report in PDF format for documentation or analysis.

Use this report to monitor ongoing discovery activities, verify successful resource detection, and analyze failures or delays observed during the discovery process.

## Move
{: #move-report}

The **Move** report provides information about move operations performed on a workgroup, allowing you to review the movement of virtual machines between sites, validate execution time, and analyze any failures that occurred during the move workflow.

> **Note**: To generate a Move report, you must first perform a move operation by clicking the **Move WorkGroup** button from the workgroup dashboard. Only after a move operation is completed is the report available to generate from the Reports page.

The report displays the following information:

- The move operation is triggered by clicking the **Move WorkGroup** button, initiating the planned or unplanned movement of the selected workgroup from one site to another.
- The move type displayed in the **Move Type** field indicates whether the operation was performed in *planned* or *unplanned* mode.
- The workgroup or VM name shown in the **Move Operation** field identifies the specific resource moved as part of the operation.
- The **No. of VMs** field displays the number of virtual machines included in the move workflow.
- The total duration of the move process shown in the **Total Time Taken** field provides the time required to complete the operation.
- The **Start Date** and **End Date** fields record the exact timestamps when the move operation began and finished.
- The bar chart in the Move report visualizes the time taken for each move execution, helping you compare move performance across multiple runs.
- The summary panel displaying **Total Move Count**, **Average No. of VMs**, **Successfully Completed**, **Failed**, and **Average time to complete** provides an overview of move operations during the selected time period.
- The **Export Summary** button enables you to download the move report in

Use this report to monitor move activities, verify successful workgroup movement across sites, and analyze failures or delays observed during the move process.

## Failover rehearsal
{: #failover-report}

The Failover Rehearsal report provides information about failover rehearsal operations performed on a workgroup, enabling you to track DR testing activities, validate VM cloning behavior, review failure reasons, and analyze the overall rehearsal duration.

> **Note**: To generate a Failover Rehearsal report, you must first run a failover rehearsal operation by selecting **Advance Operations > Failover Rehearsal** from the workgroup dashboard and completing the rehearsal workflow, only after the rehearsal finishes, the report becomes available on the **Reports** page.

The report displays the following information:

- The failover rehearsal is initiated by selecting **Advance Operations > Failover Rehearsal** from the workgroup dashboard, entering a description in the **Enter notes** field, and clicking the **Failover Rehearsal** button to start the DR testing workflow.

- The rehearsal operation name shown in the **Failover Rehearsal** header indicates the workgroup on which the rehearsal was performed and the source and target sites involved in the DR test.

- The **Status** field displays whether the failover rehearsal completed successfully or failed, helping you validate the outcome of the DR testing operation.

- The number of VMs included in the rehearsal, displayed in the **No. of VMs** column, identifies the workload size tested during the rehearsal.

- The **Approximate Time Taken** field shows the total time required for the rehearsal process, including clone creation and validation activities.

- The **Start Date** and **End Date** fields display the exact timestamps for when the rehearsal began and completed.

- The bar chart in the Failover Rehearsal report visualizes the time taken for each rehearsal execution, helping compare performance trends across multiple DR test cycles.

- The summary panel displaying **No. of Failover**, **Average No. of VMs**, and **Average time to complete** provides a consolidated view of rehearsal patterns for the selected period.

- The **Export Summary** button enables you to download the failover rehearsal report in PDF format for DR audit, compliance checks, or troubleshooting analysis.

Use this report to validate DR test readiness, verify that cloned VMs were created and tested successfully, and analyze delays or failures encountered during the failover rehearsal process.


## Cleanup
{: #cleanup-report}

The Cleanup report provides information about cleanup operations performed on a workgroup, helping you track storage cleanup activity, review status, and validate the overall cleanup duration.

> **Note:** To generate a Cleanup report, you must first run a cleanup operation by selecting **Advance Operations > Clean Up** from the workgroup dashboard and completing the cleanup process, only after the cleanup completes, the report becomes available on the **Reports** page.

The report displays the following information:

- The cleanup operation is initiated by selecting **Advance Operations > Clean Up** in the workgroup dashboard, where you enter notes in the **Enter notes** field before clicking the **Clean Up** button to start the cleanup task.

- The cleanup type indicated in the **CleanUp initiated from** header shows the time range during which the cleanup operation was executed.

- The status of the cleanup operation displayed in the **Status** column indicates whether the cleanup completed successfully or failed.

- The number of VMs involved in the cleanup shown in the **No. of VMs** field helps validate the scope of the cleanup activity.

- The total duration of the cleanup shown in the **Approximate Time Taken** field provides the execution time for the cleanup process.

- The **Start Date** and **End Date** fields capture the exact timestamps when the cleanup task began and completed.

- The bar chart in the Cleanup report visualizes the time taken for cleanup operations to help compare performance across multiple executions.

- The summary panel containing **No. of Cleanup**, **Average No. of VMs**, and **Average time to complete** provides a consolidated overview of cleanup events for the selected period.

- The **Export Summary** button enables you to download the cleanup report in PDF format for audit or troubleshooting purposes.

Use this report to monitor cleanup activities, verify whether storage cleanup actions succeeded, and analyze failures or delays observed during the cleanup process.
