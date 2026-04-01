---
copyright:
  years: 2025
lastupdated: "2026-04-01"

subcollection: dr-automation-powervs

keywords: private pod, client location

---
# Architecture for {{site.data.keyword.DR_full}} in PowerHA AIX
{: #arch-powerha-aix}

{{site.data.keyword.DR_full}} **PowerHA AIX on PowerVS** provides high availability for workloads running on IBM Power Virtual Server (PowerVS). The compute, storage, and network resources are deployed and managed by the IBM Cloud platform. PowerHA continuously monitors application and system health and automatically performs failover between cluster nodes when a failure occurs. This ensures minimal disruption to applications and helps maintain continuous availability without manual intervention.
{: shortdesc}

Explore the following sections to understand the {{site.data.keyword.DR_full_notm}} PowerHA AIX architecture, features, hardware requirements, and network configurations.

## Table of contents
{: #tocpri}

- [High-Level Architecture](#highpower)
- [DR Service broker architecture](#serviceaix)
- [Key Features](#keypro)
- [Hardware Specifications](#hspower)
- [Software Requirements](#sstpowerha)
- [Supported Storage Tiers](#sstpowerha)
- [Network Configurations](#nsaix)
- [API key](#apikey)

## High-Level Architecture
{: #highpower}

{{site.data.keyword.DR_full}}, PowerHA AIX, provides high availability for workloads running on IBM Power Virtual Server (PowerVS) in IBM Cloud. The solution uses multiple PowerVS virtual machines that are configured as a PowerHA SystemMirror cluster, with shared storage and dedicated networking to maintain application availability.

IBM Cloud manages the orchestration layer that monitors cluster health and coordinates failover operations. When an application or system failure occurs, PowerHA automatically switches workloads to a healthy node, ensuring minimal disruption and continued service availability.

This architecture enables customers to run mission-critical workloads with built-in high availability, while reducing operational complexity and eliminating the need for manual recovery actions.

![Architecture for PowerHA AIX on PowerVS](images/Power-HA-suits.drawio.svg "PowerHA AIX on PowerVS"){: caption="PowerHA AIX on PowerVS" caption-side="bottom"}

## DR Service broker architecture
{: #serviceaix}

IBM Cloud provides a managed service layer that provisions and manages PowerHA deployments on Power Virtual Server. This service layer integrates with the IBM Cloud catalog and automates the setup, configuration, and lifecycle management of high availability resources.

You interact with the service through the IBM Cloud console, APIs, or automation tools, while IBM Cloud manages the underlying orchestration and operational workflows. Failover operations are handled by PowerHA SystemMirror to ensure application availability during system or application failures.


## Key Features
{: #keypro}

- **Automated failover**
PowerHA continuously monitors application and system health. When a system or application failure occurs, workloads are automatically moved to a healthy node, minimizing downtime and maintaining service availability.

- **Data consistency with shared storage**
PowerHA uses shared storage to ensure application data remains consistent across cluster nodes. This allows workloads to resume quickly after a failover without data corruption or manual recovery steps.

- **Centralized management through IBM Cloud**
High availability configurations are managed through the IBM Cloud platform. Customers can deploy and manage PowerHA-enabled environments using the IBM Cloud console, APIs, or automation tools.

- **Usage-based billing**
PowerHA on PowerVS follows a usage-based pricing model. You are billed only for the compute and storage resources used, providing cost efficiency without the need to provision idle standby capacity.

- **Native IBM Cloud integration**
PowerHA is tightly integrated with IBM Cloud infrastructure, including networking, identity and access management, and monitoring services. This integration ensures a consistent operational experience across PowerVS environments.

- **Support for enterprise workloads**
PowerHA supports enterprise operating systems available on PowerVS, including IBM AIX®, IBM i, and Linux. This flexibility allows customers to protect a wide range of mission-critical workloads.

- **Enhanced resiliency options**
For environments that require additional resilience, PowerHA supports advanced configurations that can span multiple availability zones within a region, further improving application availability.


## Hardware Specifications
{: #hspower}

IBM Power servers that are supported by {{site.data.keyword.DR_full_notm}} include:

- **IBM Power S922**
- **IBM Power E980**
- **IBM Power E1080**
- **IBM Power S1022**
- **IBM Power E1050**


For more details, refer to the specific data sheets and hardware overview table.


## Software Requirements
{: #sstpowerha}

To deploy and use PowerHA SystemMirror on IBM Power Virtual Server (PowerVS), ensure that your environment meets the following software requirements.

- **Supported operating systems**
PowerHA supports enterprise operating systems available on PowerVS, including IBM AIX®, IBMi, and supported Linux distributions. Ensure that your virtual server instances are running a PowerHA-supported operating system level.

> **Note:** The agent installation script requires `curl` command, which is not supported for installation on **AIX 7.1**. Agent installation is supported on **AIX 7.2** and later version.

- **PowerHA System Mirror software**
PowerHA System Mirror must be installed and configured on all virtual server instances that participate in the high availability cluster. The software enables health monitoring, failover, and recovery operations.

- **IBM Cloud access and permissions**
You must have appropriate permissions in your IBM Cloud account to deploy and manage Power Virtual Server compute, storage, and networking resources required for high availability.

- **Network and storage readiness**
Virtual server instances must be configured with compatible networking and shared storage configurations to support PowerHA cluster operations.

After the software requirements are met, you can configure your PowerVS virtual server instances as a PowerHA cluster to enable high availability for your workloads.


## Supported storage tiers
{: #sst}

 PowerHA AIX offers storage with configurable IOPS levels to meet diverse HA requirements:

| Tier Level | IOPS       | Performance                                |
|------------|------------|--------------------------------------------|
| **Tier 1** | 10 IOPS/GB | Balanced performance for general workloads |
| **Tier 3** | 3 IOPS/GB  | Cost-effective for noncritical applications |
{: caption="Tier and IOPS mapping" caption-side="bottom"}

Storage is allocated based on deployment needs, ensuring efficient usage of resources and seamless management.

## API key
{: #apikey}

In PowerHA AIX, user can set up cross-account API keys to allow secure and restricted access between different IBM Cloud accounts. Cross-account API keys enable scenarios where resources or services in one account need to interact with those in another account, ensuring proper identity and access management with [IBM cloud guidelines](https://cloud.ibm.com/docs/account?topic=account-create-trusted-profile&interface=ui).


## Setting up PowerHA AIX
{: #setup}

1. Log in to your [IBM Cloud account](https://cloud.ibm.com/).
2. Locate the {{site.data.keyword.DR_full_notm}}, PowerHA AIX tile.
3. Set up storage, compute, and network resources according to HA needs.
4. Schedule HA tests and monitor system health.
