---
copyright:
  years: 2025
lastupdated: "2025-07-21"
subcollection: dr-automation
"section_updates": {
    "view_more": "/docs/dr-automation-powervs?topic=dr-automation-powervs-relnote"
}
keywords: dr-automation, release-notes
---
{{site.data.keyword.attribute-definition-list}}
# Release notes for {{site.data.keyword.DR_short}}
{: #relnote}
Use these release notes to learn about the latest updates to **{{site.data.keyword.DR_short}}** grouped by release date. Release notes are available for a minimum of three years.
{: shortdesc}


## 25 July 2025
{: #subcollection-july0725}
{: release-note}

**Advanced Operations for disaster recovery validation and control**

- **Failover Rehearsal**

Simulate a disaster recovery event without impacting production by creating a temporary rehearsal VM at the backup site. This feature helps validate DR readiness in both site and workgroup scopes. For more information, see [Failover Rehearsal](/docs/dr-automation-powervs?topic=dr-automation-powervs-ad-vance-load#Fa-il-over).

- **Clean up**

Remove temporary rehearsal VMs created during a failover rehearsal to restore the environment to its original state. For more information, see [Clean up](/docs/dr-automation-powervs?topic=dr-automation-powervs-ad-vance-load#cl-ea-nup).

- **Re‑Sync**

Synchronize backup VMs with the latest configuration and data from the active site after DR tests, rehearsals, or changes. For more information, see [Re‑Sync](/docs/dr-automation-powervs?topic=dr-automation-powervs-ad-vance-load#re-sy-nc).

**Refresh workspace option for updated topology view**

You can now use the Refresh Workspace option to update the workspace topology and display the latest managed and unmanaged VMs along with their associated workgroups. For more information, see [Refresh workspace](/docs/dr-automation-powervs?topic=dr-automation-powervs-nav-pan).

**Orchestrator external connectivity status**

A new status indicator shows whether the orchestrator can connect to all required IBM Cloud APIs and external services. This helps validate network readiness for successful DR operations. For more information, see [Orchestrator connectivity status](/docs/dr-automation-powervs?topic=dr-automation-powervs-or-ser-de).

**Shared Processor Pool configuration for virtual machines**

You can now assign a virtual machine to a shared processor pool to optimize resource usage and reduce licensing costs. Use the CLI to enable the shared processor setting during VM management or modify it later. Shared processor pools must be pre-created in the target PowerVS workspace. For more details, see [Shared Processor Pool configuration](/docs/dr-automation-powervs?topic=dr-automation-powervs-ksysmgr-commandorchestrator#es-pp-vm).

**Failover rehearsal at workgroup level**

You can now perform DR rehearsal operations at the workgroup level using the CLI, allowing safe failover simulation without impacting production workloads. This includes moving a workgroup for rehearsal and cleaning up the test environment after validation. For more details, see [Failover Rehearsal at workgroup level](/docs/dr-automation-powervs?topic=dr-automation-powervs-ksysmgr-commandorchestrator#dr-rehearsal-move-at-workgroup-level).

**Upgrade your deployment to the latest orchestrator version**

Use a snapshot to migrate your deployment to the latest orchestrator version. Create and upload the snapshot to IBM COS, then restore it on the new deployment. After migration, clean up the source cluster and delete the service. For more information, see [Upgrade your deployment](https://test.cloud.ibm.com/docs/dr-automation-powervs?topic=dr-automation-powervs-plan-work-load#upgrate-you-deployment).


**Failover rehearsal at site level**

You can now simulate a full-site failover using DR rehearsal at the site level through the CLI. This allows validation of DR readiness across all workgroups without affecting production workloads. Cleanup commands are available to reset the environment post-validation. For more details, see [Failover rehearsal at site level](/docs/dr-automation-powervs?topic=dr-automation-powervs-ksysmgr-commandorchestrator#dr-rehearsal-move-at-site-level).

## 30 April 2025
{: #subcollection-apr0425}
{: release-note}

**New option to select DR location during orchestrator deployment**
:   You can now select the DR location while configuring the orchestrator, making it easier to define the target region for orchestrator VM deployment. This enhancement provides greater control over regional DR setup. For more details, see step **Five** in [Deploying the orchestrator](/docs/dr-automation-powervs?topic=dr-automation-powervs-idep-the-orch).

**Improved selection of Power Virtual Server workspace**
:   The deployment flow now allows dynamic selection of the DR Power Virtual Server workspace based on the chosen DR location and DR Schematics workspace, ensuring better alignment of resources and reducing setup errors. For more details, see step **Seven** in [Deploying the orchestrator](/docs/dr-automation-powervs?topic=dr-automation-powervs-idep-the-orch).

**External standby orchestrator interface for high availability**
:   A new external standby orchestrator interface is now available, enabling orchestrators to recognize and manage a standby node for improved failover support and operational resilience. This feature strengthens HA capabilities by streamlining standby node configuration. For more details, see step **11** in [Deploying the orchestrator](/docs/dr-automation-powervs?topic=dr-automation-powervs-idep-the-orch).

## 31 January 2025
{: #subcollection-jan0124}
{: release-note}
**High availability for DR Orchestrator (KSYS)**
:   The DR Orchestrator (KSYS) now supports high availability in other regions, enabling continuous operations during failover. For more details, see [DR Orchestrator High Availability](/docs/dr-automation-powervs?topic=dr-automation-powervs-arch#ksys-arch).


**Improved GUI for recovery workflows**
:   Automate complex recovery workflows through the improved GUI interface, reducing manual intervention and minimizing Recovery Time Objectives (RTO). For more details, see [GUI Workflow Automation](/docs/dr-automation-powervs?topic=dr-automation-powervs-cinstance).

**Support for Power E1080 systems**
:   DR Automation now supports Power E1080 (9080-HEX) systems with up to 64 TB of memory, allowing for recovery of large-scale workloads. For more details, see [Hardware specifications](/docs/dr-automation-powervs?topic=dr-automation-powervs-arch).

**Updated external orchestrator GUI**
:   The external orchestrator GUI has been updated with new navigation and monitoring features for simplified DR setup and operation. For more details, see [Orchestrator GUI Updates](/docs/dr-automation-powervs?topic=dr-automation-powervs-manage-exter).

For more details, see the official documentation at [IBM DR Automation documentation](https://cloud.ibm.com/docs/dr-automation-powervs).
