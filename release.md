---
copyright:
  years: 2025
lastupdated: "2025-05-09"
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

## 30 April 2025
{: #subcollection-apr0425}
{: release-note}

**New option to select DR location during orchestrator deployment**
:   You can now select the DR location while configuring the orchestrator, making it easier to define the target region for orchestrator VM deployment. This enhancement provides greater control over regional DR setup. For more details, see step **5** in [Deploying the orchestrator](/docs/dr-automation-powervs?topic=dr-automation-powervs-idep-the-orch) for  more details.

**Improved selection of Power Virtual Server workspace**
:   The deployment flow now allows dynamic selection of the DR Power Virtual Server workspace based on the chosen DR location and DR Schematics workspace, ensuring better alignment of resources and reducing setup errors. For more details, see step **7** in [Deploying the orchestrator](/docs/dr-automation-powervs?topic=dr-automation-powervs-idep-the-orch) for more details.

**External standby orchestrator interface for high availability**
:   A new external standby orchestrator interface is now available, enabling orchestrators to recognize and manage a standby node for improved failover support and operational resilience. This feature strengthens HA capabilities by streamlining standby node configuration. For more details, see step **11** in [Deploying the orchestrator](/docs/dr-automation-powervs?topic=dr-automation-powervs-idep-the-orch) for more details.

## 31 January 2025
{: #subcollection-jan0124}
{: release-note}
**High availability for DR Orchestrator (KSYS)**
:   The DR Orchestrator (KSYS) now supports high availability in additional regions, enabling continuous operations during failover. For more details, see [DR Orchestrator High Availability](/docs/dr-automation-powervs?topic=dr-automation-powervs-arch#ksys-arch).


**Improved GUI for recovery workflows**
:   Automate complex recovery workflows through the improved GUI interface, reducing manual intervention and minimizing Recovery Time Objectives (RTO). For more details, see [GUI Workflow Automation](/docs/dr-automation-powervs?topic=dr-automation-powervs-cinstance).

**Support for Power E1080 systems**
:   DR Automation now supports Power E1080 (9080-HEX) systems with up to 64 TB of memory, allowing for recovery of large-scale workloads. For more details, see [Hardware specifications](/docs/dr-automation-powervs?topic=dr-automation-powervs-arch).

**Updated external orchestrator GUI**
:   The external orchestrator GUI has been updated with new navigation and monitoring features for simplified DR setup and operation. For more details, see [Orchestrator GUI Updates](/docs/dr-automation-powervs?topic=dr-automation-powervs-manage-exter).

For more details, see the official documentation at [IBM DR Automation documentation](https://cloud.ibm.com/docs/dr-automation-powervs).
