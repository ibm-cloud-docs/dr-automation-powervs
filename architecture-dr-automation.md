---
copyright:
  years: 2025
lastupdated: "2025-10-09"

subcollection: dr-automation-powervs

keywords: architecture

---

{{site.data.keyword.attribute-definition-list}}

# Architecture for {{site.data.keyword.DR_full_notm}} in IBM Data Center
{: #arch}

{{site.data.keyword.DR_full}} is located in the IBM data centers, is a robust disaster recovery solution that is designed for IBM data centers, distinct from general IBM Cloud resources. This solution uses dedicated network configurations and direct-attached storage to provide secure, reliable disaster recovery (DR) capabilities.
{: shortdesc}

Explore the following sections to understand the {{site.data.keyword.DR_full_notm}} architecture, features, hardware requirements, and network configurations.

## Table of contents
{: #toc}

- [High-Level Architecture](#high)
- [DR Service broker architecture](#service-broker)
- [DR Orchestrator (KSYS) architecture](#ksys-arch)
- [Key Features](#key)
- [Hardware Specifications](#hs)
- [Supported Storage Tiers](#sst)
- [Network Configurations](#ns)


## High-Level architecture
{: #high}

The **{{site.data.keyword.DR_full_notm}}** system operates within IBM Power Virtual data centers, which are isolated from the core IBM Cloud environment. Using dedicated networks and direct-attached storage ensures secure, high-performance disaster recovery (DR) capabilities tailored for fast, reliable workload recovery.

Central to this architecture is the **Service Broker**, which manages compute, storage, and network resources to streamline and automate DR processes. It simplifies recovery setup, enabling customers to quickly deploy and manage DR services through an intuitive interface.

The **Orchestrator (KSYS)** is crucial in coordinating DR workflows, ensuring virtual machines (VMs) are brought online in the correct order during recovery. This automation minimizes downtime and data loss, helping organizations confidently meet their Recovery Time Objectives (RTOs) and Recovery Point Objectives (RPOs).

This setup provides a secure, seamless DR solution that integrates with your production environment, enabling smooth failover and failback to maintain business continuity in unexpected events.

![DR Automation Architecture](images/updated.svg "DR Automation Architecture"){: caption="DR Automation Architecture" caption-side="bottom"}

## DR Service broker architecture
{: #service-broker}

The **DR Service Broker** within IBM Cloud is central to provisioning and managing DR orchestration for PowerVS. Operating as a dedicated component, it handles critical functions, including billing, resource management, and service orchestration.

### Service provisioning
{: #serv-pro}

The Service Broker deploys the DR Orchestrator (KSYS) VM within the PowerVS workspace, using PowerVS APIs to establish and manage DR operations. This process enables seamless integration of DR orchestration capabilities specific to each user account.

### Connectivity and communication
{: #Conn}

Through IBM Cloud VPN and VPC services, the DR Orchestrator communicates securely with the Service Broker. Connections from external clients or users are routed through IBM’s secure networking layers to ensure high availability and low latency during DR operations.

### Resource management and billing integration
{: #resource}

The Service WebSphere Message Broker updates DR metrics to IBM’s billing system (BSS) based on individual instances, providing granular billing data per customer. It ensures that usage is reported accurately for each instance and maintains a high level of automation in resource accounting.

### Interface accessibility
{: #inter}

The {{site.data.keyword.DR_short}} Service Broker, accessible via the IBM Cloud GUI, allows users to manage DR settings through a standardized interface. This design enhances user experience and aligns with IBM’s broader catalog for resource provisioning.

## DR Orchestrator (KSYS) architecture
{: #ksys-arch}

The **DR Orchestrator (KSYS)**, acting as the operational core within user accounts, is critical in running and managing DR workflows, specifically for PowerVS instances. This component manages the deployment, configuration, and operation of VMs required during DR.

### VM Orchestration and workflow management
{: #vmorch}

KSYS brings VMs online in the required sequence during a disaster, minimizing RTO and RPO. This workflow automation ensures systematic failover and recovery, essential for maintaining business continuity.

### Custom metrics and monitoring
{: #custom}

KSYS regularly updates custom DR metrics, securely transmitting to the Service Broker by using DR Automation API and adhering to authentication protocols. This allows ongoing monitoring and helps identify and address anomalies in real-time. These metric data can be reviewed in IBM Cloud Monitor with Power Virtual Server DR Automation dash board and you can see the metric name `managed_vm_count` that shows for each deployment how many number of managed VMs are enabled for DR. For More details click [IBM cloud monitoring](https://cloud.ibm.com/docs/monitoring?topic=monitoring-getting-started).

### Provisioning and configuration management
{: #provision}

The Service Broker provisioning capabilities allow KSYS to configure with essential user inputs and monitored to ensure alignment with the recovery environment. Also, it offers a GUI URL accessible through IBM’s catalog, enabling users to monitor and manage configurations in real-time.

### High availability (Optional)
{: #ha}

For enhanced resilience, KSYS supports High Availability (HA) setup, ensuring continuous operation and reducing single points of failure.

## Key features
{: #key}

### Simplified disaster recovery management
{: #simplify}

{{site.data.keyword.DR_short}} provides a single interface to manage DR processes for IBM PowerVS environments. Key features include:

Automated failover and failback
:   Automate the failover process, ensuring that workloads resume quickly in the backup environment.

Scheduling and monitoring
:   Schedule DR operations and monitor the health and status of DR sites.

Customizable recovery settings
:   Define recovery priorities and configurations for different VMs or applications.

### Flexible billing model
{: #flex}

{{site.data.keyword.DR_short}} follows a usage-based billing model, with flexible options based on the selected resources and configurations.
The IBM Cloud catalog supports accurate billing and comprehensive reporting, ensuring that customers have clear visibility into DR-related costs.




## Hardware specifications
{: #hs}

IBM Power servers that are supported by {{site.data.keyword.DR_full_notm}} include:

- **IBM Power S922**
- **IBM Power E980**
- **IBM Power E1080**
- **IBM Power S1022**
- **IBM Power11**

For more details, refer to the specific data sheets and hardware overview table.

## Software requirements
{: #sr}

- The Orchestrator (KSYS) Power Virtual Server instance is deployed with 0.5 cores and 4 GB of memory however, larger environments with over 100 VMs require more resources. You can increase this configuration after the initial deployment by modifying power virtual server properties with in the workspace.

- The KSYS logical partition runs IBM® AIX® 7.3 with Technology Level 2 Service Pack 1 (7300-02-01).

- IBM Power Virtual Server Public Cloud officially supports Red Hat Enterprise Linux (RHEL), IBM i, and IBM AIX® operating systems for creating virtual servers and configuring them as managed virtual machines to enable DR.

The configuration is complete, you can add all the supported Power Virtual Server instances as Managed VMs to enable DR.

## API key
{: #apikey}

In {{site.data.keyword.DR_short}}, user can set up cross-account API keys to allow secure and restricted access between different IBM Cloud accounts. Cross-account API keys enable scenarios where resources or services in one account need to interact with those in another account, ensuring proper identity and access management with [IBM cloud guidelines](https://cloud.ibm.com/docs/account?topic=account-create-trusted-profile&interface=ui).

## Supported storage tiers
{: #sst}

{{site.data.keyword.DR_short}} offers storage with configurable IOPS levels to meet diverse DR requirements:

| Tier Level | IOPS       | Performance                                |
|------------|------------|--------------------------------------------|
| **Tier 1** | 10 IOPS/GB | Balanced performance for general workloads |
| **Tier 3** | 3 IOPS/GB  | Cost-effective for noncritical applications |
{: caption="Tier and IOPS mapping" caption-side="bottom"}

Storage is allocated based on deployment needs, ensuring efficient usage of resources and seamless management.


## Network configurations
{: #ns}

### Connectivity for Orchestrator UI:
{: #cfoui}

As part of the DR Automation deployment, the system creates the Orchestrator (KSYS) virtual server with private networks only, preventing direct access to the Power Virtual Server. To access this virtual server, you must use a VPN connected to the VPC or manually enable the public network after deployment.

DR Automation use a VPC schematic through the **Power Virtual Server with VPC landing zone**, this internally creates an optional VPN. This VPN allows you to connect the Power Virtual Server and Virtual Server Instances (VSI) by downloading the VPN profile.

After deployment, you can launch the "External Orchestrator UI" when you connect to the VPN, or when the public network is explicitly enabled.

When KSYSHA is enabled, a standby Orchestrator is created in the user selected workspace, and it automatically adds this workspace to the Transit Gateway to establish connectivity with the VPC. When selecting the standby workspace, ensure that no duplicate subnet range is configured across the workspaces connected to the Transit Gateway. If multiple Power Virtual Servers have the same subnet range, they may fail to communicate with the VPC.

Additionally, the system automatically adds all default networks configured for Power Virtual Servers to the security group to enable communication during the **Power Virtual Server with VPC landing zone** creation. If you create new subnets in the Power Virtual Server workspace, you must add them to the security group to enable communication with the VPC. For more details, refer to [VPC Security](https://cloud.ibm.com/docs/vpc?topic=vpc-security-in-your-vpc).

 For detailed steps on connecting to the Power Virtual Server with VPC, refer to [Connect using a client-to-site VPN](https://cloud.ibm.com/docs/powervs-vpc?topic=powervs-vpc-solution-connect-client-vpn).

## Setting Up {{site.data.keyword.DR_short}}
{: #setup}

1. Log in to your [IBM Cloud account](https://cloud.ibm.com/).
2. Locate the {{site.data.keyword.DR_full_notm}} tile.
3. Set up storage, compute, and network resources according to DR needs.
4. Schedule DR tests and monitor system health.
