---
front_matter_title: "Getting started with IBM DR automation for PowerVS"
lastupdated: "2024-10-23"
copyright: "2023, 2024"
subcollection: dr-automation
---
# Getting started with IBM® DR Automation for PowerVS

IBM® VM Recovery Manager (VMRM) **DR automation** is an IBM PowerVS disaster recovery offering. You can use **DR automation for PowerVS** to automate disaster recovery (DR) processes for virtualized environments, ensuring continuity of operations with minimal manual intervention in the event of disasters or disruptions.

With **DR automation**, you can quickly deploy a disaster recovery solution from the IBM Cloud Catalog UI, which provides an intuitive interface to select and configure recovery services. The solution automates the recovery of virtual machines (VMs) and workloads, leveraging IBM Cloud infrastructure to offer a flexible, scalable, and efficient DR process. You can provision DR capabilities that synchronize data and manage replication between sites to secure critical workloads.

You get robust, automated management that continuously monitors DR operations, reduces manual processes, and minimizes downtime. The **DR automation** solution supports IBM Cloud's global regions, offering low-latency failover capabilities and high availability options to meet your specific DR needs across multiple IBM Cloud locations. By using **DR automation for PowerVS**, you can simplify the DR setup and operation, leveraging IBM Cloud’s infrastructure to enhance business resilience.

Get started with **DR automation for PowerVS** today to ensure reliable and efficient disaster recovery for your business workloads. For frequently asked questions about DR automation, see the (FAQ)[].

## Terminology

**IBM Cloud account** - You can log on to the IBM Cloud dashboard by using an IBM Cloud account to access various IBM Cloud solutions, services, and offerings. To create an IBM Cloud account, see [Signing up for the IBM Cloud](https://cloud.ibm.com/registration).

**Location and region** - The global network of locations in IBM Cloud provides three tiers of regions: multizone regions (MZR), single-campus multizone regions, and data centers. To achieve low application latency, choose your nearest location and region. For details about the available IBM Cloud regions and data centers, review [Region and data center locations for resource deployment](https://cloud.ibm.com/docs/overview?topic=overview-locations).

**Workspace** - A workgroup is a logical grouping of virtual machines, storage volumes, network configurations, and other resources within a defined geographic region. Workgroups are accessible from the Power Virtual Server user interface, allowing users to organize and manage multiple Power Virtual Server instances for specific purposes, such as production or development testing. Within each designated site, users can establish multiple workgroups to facilitate environment-specific operations, streamline resource allocation, and ensure seamless disaster recovery processes, including failover and failback capabilities.

**DR Service Broker** - The DR Service Broker provides a centralized interface within IBM Cloud to manage and coordinate the DR services and resources across multiple environments. It simplifies DR configurations, resource allocations, and service accessibility, streamlining disaster recovery setup and maintenance across PowerVS instances.

**DR Orchestrator (KSYS)** - The DR Orchestrator, also known as KSYS, is the central management component responsible for automating disaster recovery processes within PowerVS. KSYS manages and coordinates failover, failback, and synchronization of resources across sites, ensuring efficient and reliable DR operations.
