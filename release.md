---
copyright:
  years: 2025
lastupdated: "2026-04-30"
subcollection: dr-automation-powervs
"section_updates": {
    "view_more": "/docs/dr-automation-powervs?topic=dr-automation-powervs-relnote"
}
keywords: release-notes, new features, enhancements, latest release
---

{{site.data.keyword.attribute-definition-list}}
# Release notes for {{site.data.keyword.DR_short}}
{: #relnote}

Use the release notes to learn about the latest updates to **{{site.data.keyword.DR_short}}** grouped by release date. Release notes are available for a minimum of three years.
{: shortdesc}


## 30 April 2026
{: #subcollection-april30206}
{: release-note-april}

- The service is renamed from DR Automation for Power Virtual Server to {{site.data.keyword.DR_full}}. This update reflects the addition of high-availability capabilities along with existing disaster recovery features. No changes are required for existing deployments. For more information, see [Getting started with PowerHA Automation for Power Virtual Server](/docs/dr-automation-powervs?topic=dr-automation-powervs-getting-started-with-powerha-automation-for-power-virtual-server).

- PowerHA is now available as part of HA and DR Automation for Power Virtual Server, enabling you to deploy and manage high-availability clusters by using PowerHA SystemMirror. This capability is available through the PowerHA AIX for PowerVS plan. The solution uses multiple PowerVS virtual machines that are configured as a cluster with shared storage and dedicated networking, while IBM Cloud manages the orchestration layer for monitoring and failover operations. For more information, see [Architecture for HA and DR Automation for IBM® Power™ Virtual Server for PowerHA](/docs/dr-automation-powervs?topic=dr-automation-powervs-arch-powerha-aix).

- Monitoring and Activity Tracker support is now available for PowerHA SystemMirror in IBM Cloud.For more information, see [PowerHA observability](/docs/dr-automation-powervs?topic=dr-automation-powervs-monitoring-metrics-for-powerha-systemmirror)

- API, SDK, CLI, Terraform support is now available for PowerHA operations, You can manage service instance configuration, cluster nodes, and deployment lifecycle by using supported commands. You can also retrieve events, download agents, and view PowerVS workspaces and locations for the service instance, allowing better automation and operational control. For more information, see [HA and DR Automation for IBM® Power™ Virtual Server command reference](/docs/dr-automation-powervs?group=ha-and-dr-automation-for-ibm-power-virtual-server-command-reference).

- You can now configure VM Flex capacity by using the external orchestrator UI and CLI, allowing the orchestrator (KSYS) to dynamically adjust CPU and memory allocation for backup VMs during failover and disaster recovery rehearsal operations. Backup VMs are initially provisioned with minimal resources and scaled based on configured flex values during operations, optimizing resource utilization in the target PowerVS workspace. For more information, see [Flex capacity support](/docs/dr-automation-powervs?topic=dr-automation-powervs-comm#flex-capacity-support).

- Dedicated host support is now available in {{site.data.keyword.DR_full}}, enabling you to deploy backup VMs on a specific PowerVS dedicated host or host group at the target site by using the UI and CLI. This enhancement provides better control over VM placement, improved resource isolation, and optimized resource utilization in the backup environment. You can identify available dedicated hosts and host groups and specify the required host or host group while managing a VM. For more information, see [Dedicated host support](/docs/dr-automation-powervs?topic=dr-automation-powervs-comm#dedicated-host).

- Target VM name support is now available in {{site.data.keyword.DR_full}}, enabling you to specify a custom name for the backup VM created at the target site by using the UI and CLI. This enhancement provides greater flexibility in naming conventions and improves VM identification and management across environments. You can define the target VM name during the VM management operation instead of using the default_BackUp suffix. For more information, see [Target VM name support](/docs/dr-automation-powervs?topic=dr-automation-powervs-comm#backup-vm-rename).


## 05 December 2025
{: #subcollection-december1225}
{: release-note-october}

- You can now deploy the orchestrator with minimal inputs. You no longer need to provide schematic or custom VPC details. The orchestrator uses a private endpoint to communicate with all required IBM Cloud services. For more information, see [Deploying the orchestrator](/docs/dr-automation-powervs?topic=dr-automation-powervs-idep-the-orch).
- You can now enable Multi-Factor Authentication (MFA) for the DR automation orchestrator to enhance login security. For more information, see [Multifactor authentication](/docs/dr-automation-powervs?topic=dr-automation-powervs-multifactor-authentication).
- You can now assign roles to users and manage permissions through the new User Role Management feature, which introduces role-based access control (RBAC) for creating users, defining roles, and controlling access to DR automation operations. For more information, see [User role management](/docs/dr-automation-powervs?topic=dr-automation-powervs-user-ro-mang).
- You can now generate consolidated operational reports for the external orchestrator, including Discovery, Move, Failover Rehearsal, and Cleanup activities. For more information, see [Generate external orchestrator reports](/docs/dr-automation-powervs?topic=dr-automation-powervs-reports).
- You can now map multiple networks for each VM during network pairing, allowing more flexible and granular connectivity configuration across workgroups. For more information, see [Creating network pairing](/docs/dr-automation-powervs?topic=dr-automation-powervs-network-pairing).
- You can now manage custom SSL certificates and private-key pairs for GUI communication. For more information, see [GUI certificate and private-key pairs](/docs/dr-automation-powervs?topic=dr-automation-powervs-gui-certificates).

## 16 October 2025
{: #subcollection-october1025}
{: release-note-october}


- You can now deploy and manage your DR Automation resources in a private (client) cloud environment by using IBM PowerVS Satellite locations. This update introduces the complete architecture, deployment flow, and configuration details for setting up DR Automation in client locations, including information about the Service Broker, KSYS orchestrator, storage tiers, and network connectivity. For more information, see [Deploy DR Automation in Your private cloud environment](/docs/dr-automation-powervs?topic=dr-automation-powervs-arch-private-pod).

- You can now view the deployment timestamps for both the primary and standby orchestrators, along with the subscription plan details (Public or Private) selected during initial setup. These enhancements provide better tracking of deployment history and service configuration. For more information, see [Orchestrator and service details](/docs/dr-automation-powervs?topic=dr-automation-powervs-or-ser-de).

- In the Orchestrator UI Configuration deployment page, the Modify VM option is provided, which allows you to modify, configure multiple IP mappings, and enable the Shared processor Pool (SPP) to optimize performance and resource utilization for the DR-enabled virtual machines. For more information, see [Managing VM sessions](/docs/dr-automation-powervs?topic=dr-automation-powervs-manage-vm-ses#modify-vm-ses), [Shared processor pool support for public, and private plans](/docs/dr-automation-powervs?topic=dr-automation-powervs-comm#shared-processor-pool-configuration).

- DR Automation now displays real-time notifications for events, including deployment status, errors, and operational updates. Each notification appears as a pop-up with a timestamp, and you can track up to 100 current events, providing clear visibility into system activities and changes. For more information, see [administering event logs](/docs/dr-automation-powervs?topic=dr-automation-powervs-manage-log#adm-log).

- When deploying the orchestrator with Client Location (Private pod), the Add Sites page now displays Select Source Satellite Location and Select Target Satellite Location instead of region-based options. For more information, see [Add sites to KSYS](/docs/dr-automation-powervs?topic=dr-automation-powervs-con-site-ksys).

- DR Automation now supports upgrading the orchestrator ksys file sets through a simplified CLI command, ensuring that your system remains up to date with the latest features, fixes, and security enhancements. For more information, see [Migrate using ksysmgr commands](/docs/dr-automation-powervs?topic=dr-automation-powervs-Upgrade-fil-set).

- You can now choose Orchestrator HA enablement in the DR configuration page. For more information, see [Deploying the orchestrator for disaster recovery](/docs/dr-automation-powervs?topic=dr-automation-powervs-idep-the-orch).

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

You can now use the Refresh workspace option to update the workspace topology and display the latest managed and unmanaged VMs along with their associated workgroups. For more information, see [Refresh workspace](/docs/dr-automation-powervs?topic=dr-automation-powervs-nav-pan).

**Orchestrator external connectivity status**

A new status indicator shows whether the orchestrator can connect to all required IBM Cloud APIs and external services. This helps validate network readiness for successful DR operations. For more information, see [Orchestrator connectivity status](/docs/dr-automation-powervs?topic=dr-automation-powervs-or-ser-de).

**Shared processor Pool configuration for virtual machines**

You can now assign a virtual machine to a shared processor pool to optimize resource usage and reduce licensing costs. Use the CLI to enable the shared processor setting during VM management or modify it later. Shared processor pools must be pre-created in the target PowerVS workspace. For more details, see [Shared processor Pool configuration](/docs/dr-automation-powervs?topic=dr-automation-powervs-ksysmgr-commandorchestrator#es-pp-vm).

**Failover rehearsal at workgroup level**

You can now perform DR rehearsal operations at the workgroup level using the CLI, allowing safe failover simulation without impacting production workloads. This includes moving a workgroup for rehearsal and cleaning up the test environment after validation. For more details, see [Failover Rehearsal at workgroup level](/docs/dr-automation-powervs?topic=dr-automation-powervs-ksysmgr-commandorchestrator#dr-rehearsal-move-at-workgroup-level).

**Upgrade your deployment to the latest orchestrator version**

Use a snapshot to migrate your deployment to the latest orchestrator version. Create and upload the snapshot to IBM Cloud Object Storage, then restore it on the new deployment. After migration, clean up the source cluster and delete the service. For more information, see [Upgrade your deployment](https://cloud.ibm.com/docs/dr-automation-powervs?topic=dr-automation-powervs-plan-work-load#upgrate-you-deployment).


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
Automate complex recovery workflows via an improved GUI, reducing manual intervention and minimizing Recovery Time Objectives (RTO). For more details, see [GUI Workflow Automation](/docs/dr-automation-powervs?topic=dr-automation-powervs-cinstance).

**Support for Power E1080 systems**
:   DR Automation now supports Power E1080 (9080-HEX) systems with up to 64 TB of memory, allowing for recovery of large-scale workloads. For more details, see [Hardware specifications](/docs/dr-automation-powervs?topic=dr-automation-powervs-arch).

**Updated external orchestrator GUI**
:   The external orchestrator GUI with new navigation and monitoring features for simplified DR setup and operation. For more details, see [Orchestrator GUI Updates](/docs/dr-automation-powervs?topic=dr-automation-powervs-manage-exter).

For more details, see the official documentation at [IBM DR Automation documentation](https://cloud.ibm.com/docs/dr-automation-powervs).
