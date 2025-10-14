---
copyright:
  years: 2025
lastupdated: "2025-10-14"

subcollection: dr-automation

keywords: private pod, client location

---


{{site.data.keyword.attribute-definition-list}}

# Architecture for {{site.data.keyword.DR_full_notm}} in Client Location (Private Cloud)
{: #arch-private-pod}

{{site.data.keyword.DR_full}} automatically orchestrates disaster recovery for managed workloads from your data center (Client location). The infrastructure, compute, storage, and network are physically deployed at your location (Client location) and managed by IBM Cloud platform. DR automation is available only if your environment supports Geo-Redundant Storage (GRS), which replicates data across geographically separated sites. With GRS configured, the solution automatically triggers failover and recovery operations, reducing downtime and ensuring business continuity without manual intervention.
{: shortdesc}




Explore the following sections to understand the {{site.data.keyword.DR_full_notm}} for client location architecture, features, hardware requirements, and network configurations.


## Table of contents
{: #toc-pri}

- [High-Level Architecture](#high)
- [DR Service broker architecture](#service-broker)
- [DR Orchestrator (KSYS) architecture](#ksys-arch)
- [Key Features](#key)
- [Hardware Specifications](#hs)
- [Supported Storage Tiers](#sst)
- [Network Configurations](#ns)
- [Data center capabilities](#data-center-capabilities)


## High-Level architecture
{: #high-private}

The **{{site.data.keyword.DR_full_notm}}** system operates within IBM Power Virtual data centers, which are isolated from the core IBM Cloud environment. Using dedicated networks and direct-attached storage ensures secure, high-performance disaster recovery (DR) capabilities tailored for fast, reliable workload recovery.

Central to this architecture is the **Service Broker**, which manages compute, storage, and network resources to streamline and automate DR processes. The Service Broker simplifies recovery setup, enabling customers to quickly deploy and manage DR services through an intuitive interface.

The **Orchestrator (KSYS)** is crucial in coordinating DR workflows, ensuring virtual machines (VMs) are brought online in the correct order during recovery. This automation minimizes downtime and data loss, helping organizations confidently meet their Recovery Time Objectives (RTOs) and Recovery Point Objectives (RPOs).

This setup provides a secure, seamless DR solution that integrates with your production environment, enabling smooth failover and failback to maintain business continuity in unexpected events.

![DR Automation Architecture](images/private-pod.svg "architecture-diagrams-deployment-private-pod"){: caption="DR Automation Architecture for Client location" caption-side="bottom"}

## DR Service broker architecture
{: #service-broker-private}

The **DR Service Broker** within IBM Cloud is central to provisioning and managing DR orchestration for PowerVS. Operating as a dedicated component, The DR Service Broker handles critical functions, including billing, resource management, and service orchestration.

### Service provisioning
{: #serv-pro-private}

The Service Broker deploys the DR Orchestrator (KSYS) VM within the PowerVS workspace, by using PowerVS APIs to establish and manage DR operations. This process enables seamless integration of DR orchestration capabilities specific to each user account.

### Connectivity and communication
{: #Conn-private}

Through IBM Cloud VPN and VPC services, the DR Orchestrator communicates securely with the Service Broker. Connections from external clients or users are routed through the secure networking layers of IBM to ensure high availability and low latency during DR operations.

### Resource management and billing integration
{: #resource-private}

The Service WebSphere Message Broker updates DR metrics to IBM’s billing system (BSS) of IBM that is based on individual instances, providing granular billing data per customer. This process ensures that usage is reported accurately for each instance and maintains a high level of automation in resource accounting.

### Interface accessibility
{: #inter-private}

The {{site.data.keyword.DR_short}} Service Broker, accessible by using the IBM Cloud GUI, allows users to manage DR settings through a standardized interface. This design enhances user experience and aligns with the IBM broader catalog for resource provisioning.

## DR Orchestrator (KSYS) architecture
{: #ksys-arch-private}

The **DR Orchestrator (KSYS)**, acting as the operational core within user accounts, is critical in running and managing DR workflows, specifically for PowerVS instances. This component manages the deployment, configuration, and operation of VMs required during DR.

### VM Orchestration and workflow management
{: #vmorch-private}

KSYS brings VMs online in the required sequence during a disaster, minimizing Recovery Time Objective and Recovery Point Objective. This workflow automation ensures systematic failover and recovery, essential for maintaining business continuity.

### Custom metrics and monitoring
{: #custom-private}

KSYS regularly updates custom DR metrics, securely transmitting to the Service Broker by using DR Automation API and adhering to authentication protocols. This process allows ongoing monitoring and helps identify and address anomalies in real-time. These metric data can be reviewed in the IBM Cloud Monitor with Power Virtual Server DR Automation dashboard you can see the metric name `managed_vm_count` that shows for each deployment how many number of managed VMs are enabled for DR. For More information, see [IBM cloud monitoring](https://cloud.ibm.com/docs/monitoring?topic=monitoring-getting-started).

### Provisioning and configuration management
{: #provision-private}

The Service Broker provisioning capabilities allow KSYS to configure with essential user inputs and monitor to ensure alignment with the recovery environment. Also, it offers a GUI URL accessible through IBM catalog, enabling users to monitor and manage configurations in real-time.

### High availability (Optional)
{: #ha-private}

For enhanced resilience, KSYS supports **High Availability (HA)** setup through Dr automation deployment, ensuring continuous operation and reducing single points of failure.

## Key features
{: #key-private}

### Simplified disaster recovery management
{: #simplify-private}

{{site.data.keyword.DR_short}} provides a single interface to manage DR processes for IBM PowerVS environments, and include the following key features:

Automated failover and failback
:   Automate the failover process, ensuring that workloads resume quickly in the backup environment.

Scheduling and monitoring
:   Schedule DR operations and monitor the health and status of DR sites.

Customizable recovery settings
:   Define recovery priorities and configurations for different VMs or applications.

### Flexible billing model
{: #flex-private}

{{site.data.keyword.DR_short}} follows a usage-based billing model, with flexible options that are based on the selected resources and configurations.
The IBM Cloud catalog supports accurate billing and comprehensive reporting, ensuring that customers have clear visibility into DR-related costs.

## Hardware specifications
{: #hs-private}

IBM Power servers supported by {{site.data.keyword.DR_full_notm}} include the following models. However, all Power Virtual Server machine types are supported by DR automation.

- **IBM Power S922**
- **IBM Power E980**
- **IBM Power E1080**
- **IBM Power S1022**
- **IBM Power E1050**
- **IBM Power S1122**
- **IBM Power E1150**
- **IBM Power S1124**

For more details, see to the specific data sheets and hardware overview table.

## Software requirements
{: #sr-private}

- The Orchestrator (KSYS) Power Virtual Server instance is deployed with 0.5 cores and 4 GB of memory. However, larger environments with over 100 VMs require more resources. You can increase this configuration after the initial deployment by modifying power virtual server properties with in the workspace.

> - **Current Baseline**: Newly deployed KSYS logical partitions run IBM® AIX® 7.3 with Technology Level 2 Service Pack 1 (**7300-02-01**).

> - **Older Deployments**:Existing deployments may be running earlier Technology Levels or Service Packs prior to **7300-02-01**, so you should verify their deployment level and plan upgrades if needed.

- IBM Power Virtual Server private cloud officially supports Red Hat Enterprise Linux (RHEL), IBM i, and IBM AIX® operating systems for creating virtual servers and configuring them as managed virtual machines to enable DR.

After the configuration is complete, you can add all the supported Power Virtual Server instances as Managed VMs to enable DR


## API key
{: #apikey-private}

In {{site.data.keyword.DR_short}}, you can set up cross-account API keys to allow secure and restricted access between different IBM Cloud accounts. Cross-account API keys enable scenarios where resources or services in one account need to interact with those in another account, ensuring proper identity and access management with [IBM cloud guidelines](https://cloud.ibm.com/docs/account?topic=account-create-trusted-profile&interface=ui).

## Supported storage tiers
{: #sst-private}

{{site.data.keyword.DR_short}} offers storage with configurable IOPS levels to meet diverse DR requirements:

| Tier Level | IOPS       | Performance                                |
|------------|------------|--------------------------------------------|
| **Tier 1** | 10 IOPS/GB | Balanced performance for general workloads |
| **Tier 3** | 3 IOPS/GB  | Cost-effective for noncritical applications |
{: caption="Tier and IOPS mapping" caption-side="bottom"}

Storage is allocated based on deployment needs, ensuring efficient usage of resources and seamless management.

## Satellite location
{: #sat-location}
The Satellite location is where the private cloud VM is hosted, for which the Power Virtual Server disaster recovery is enabled in a DR automation Private Cloud architecture. This Satellite location corresponds to the IBM Cloud region closest to your data center, with a recommended network round-trip time (RTT) of 200 milliseconds or less. For more information about available Satellite locations, see [IBM Satellite location](/docs/dr-automation-powervs?topic=dr-automation-powervs-ibm-satellite-location).


## Network configurations
{: #ns-private}

### Connectivity for Orchestrator UI:
{: #cfoui-private}

As part of the DR Automation deployment, the system creates the Orchestrator (KSYS) virtual server with private networks only, preventing direct access to the Power Virtual Server. To access this virtual server, you must use a VPN that is connected to the VPC or manually enable the public network after deployment.

DR Automation uses **custom VPC** and **VPC schematic** through the Power Virtual Server with VPC landing zone , VPC Schematic internally creates an optional VPN  and in case of Custom VPC, VPN need to be configured manually. This VPN allows you to connect the Power Virtual Server and Virtual Server Instances (VSI) by downloading the VPN profile.

After deployment, you can launch the **External Orchestrator UI** when you connect to the VPN, or when the public network is explicitly enabled.

When KSYSHA is enabled, a standby Orchestrator is created in the user selected workspace, and the workspace is added to the Transit Gateway to establish connectivity with the VPC. When selecting the standby workspace, ensure that no duplicate subnet range is configured across the workspaces that are connected to the Transit Gateway. If multiple Power Virtual Servers have the same subnet range, the subnets they might fail to communicate with the VPC.

Additionally, the system automatically adds all default networks that are configured for Power Virtual Servers to the security group to enable communication during the **Power Virtual Server with VPC landing zone** creation. If you create new subnets in the Power Virtual Server workspace, you must add them to the security group to enable communication with the VPC. For more information about VPC, see [VPC Security](https://cloud.ibm.com/docs/vpc?topic=vpc-security-in-your-vpc).

 For detailed steps on connecting to the Power Virtual Server with VPC, see [Connect using a client-to-site VPN](https://cloud.ibm.com/docs/powervs-vpc?topic=powervs-vpc-solution-connect-client-vpn).

## Data center capabilities
{: #data-center-capability}

You can check and compare the data center capabilities among three different infrastructure locations on the overview page of the [IBM Power Virtual Server DR Automation](https://cloud.ibm.com/catalog/services/power-virtual-server-dr-automation?catalog_query=aHR0cHM6Ly9jbG91ZC5pYm0uY29tL2NhdGFsb2c%2Fc2VhcmNoPVBvd2VyVlMjc2VhcmNoX3Jlc3VsdHM%3D#:~:text=IBM%20Power%20Virtual%20Server%20DR,operations%20with%20minimal%20manual%20intervention.) in the IBM Cloud console. You can also use the external interfaces such as API, CLI, and Terraform to check your data center capabilities.

For example, you can determine the support for the following capabilities in your infrastructure:

- Machine types (Power11)
- Global Replication Service (GRS)

## Setting Up {{site.data.keyword.DR_short}}
{: #setup-private}

1. Log in to your [IBM Cloud account](https://cloud.ibm.com/).
2. Locate the {{site.data.keyword.DR_full_notm}} tile.
3. Set up storage, compute, and network resources according to DR needs.
4. Schedule DR tests and monitor system health.
