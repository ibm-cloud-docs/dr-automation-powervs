---
front_matter_title: "DR Automation for PowerVS Architecture"
lastupdated: "2024-10-23"
copyright: "2023, 2024"
subcollection: dr-automation
---
# Architecture for IBM DR Automation for PowerVS

IBM® DR Automation for PowerVS is a robust disaster recovery solution specifically designed for IBM data centers, distinct from general IBM Cloud resources. This solution leverages dedicated network configurations and direct-attached storage to provide secure, reliable disaster recovery (DR) capabilities.

The IBM Cloud Service Framework facilitates seamless deployment and management of DR Automation for PowerVS by integrating key components such as the Service Broker, Resource Management Controller (RMC), and IBM Cloud Catalog. This framework streamlines the DR setup process, enhances security, and ensures compliance, delivering a comprehensive DR solution within the IBM Cloud infrastructure.

Explore the following sections to understand the DR Automation for PowerVS architecture, features, hardware requirements, and network configurations.

## Table of Contents

- [High-Level Architecture](#high-level-architecture)
- [Key Features](#key-features)
- [IBM Cloud Service Framework](#ibm-cloud-service-framework)
- [Hardware Specifications](#hardware-specifications)
- [Supported Storage Tiers](#supported-storage-tiers)
- [Network Configurations](#network-configurations)

---

## High-Level Architecture

The **DR Automation for PowerVS** system operates within IBM data centers, isolated from the core IBM Cloud environment. Utilizing dedicated networks and direct-attached storage ensures secure, high-performance disaster recovery (DR) capabilities tailored for fast, reliable workload recovery.

Central to this architecture is the **Service Broker**, which manages compute, storage, and network resources to streamline and automate DR processes. It simplifies recovery setup, enabling customers to quickly deploy and manage DR services through an intuitive interface.

The **Orchestrator (KSYS)** is crucial in coordinating DR workflows, ensuring Virtual Machines (VMs) are brought online in the correct order during recovery. This automation minimizes downtime and data loss, helping organizations confidently meet their **Recovery Time Objectives (RTOs)** and **Recovery Point Objectives (RPOs)**.

This setup provides a secure, seamless DR solution that integrates with your production environment, enabling smooth failover and failback to maintain business continuity in case of unexpected events.


---

## Key Features

### Simplified Disaster Recovery Management

DR Automation for PowerVS provides a single interface to manage DR processes for IBM PowerVS environments. Key features include:

- **Automated Failover and Failback**:
Automate the failover process, ensuring that workloads resume quickly in the backup environment.

- **Scheduling and Monitoring**:
Schedule DR operations and monitor the health and status of DR sites.

- **Customizable Recovery Settings**:
Define recovery priorities and configurations for different VMs or applications.

### IBM Cloud Service Framework Integration

The **IBM Cloud Service Framework** provides a streamlined experience for disaster recovery (DR) automation. At the heart of this framework, the **Service Broker** manages resources for compute, storage, and network, enabling users to select DR services from the **IBM Cloud Catalog** and specify deployment parameters with ease. The **Resource Management Controller (RMC)** automates provisioning tasks and configures VMs for DR, ensuring a seamless and intuitive user experience.

Additional IBM Cloud services, such as Activity Tracker, IBM LogDNA, Cloud Object Storage (COS), and Key Management, support the DR solution by enhancing security, auditability, and compliance. These services are interconnected through secure, redundant network paths, providing a reliable and resilient environment for business continuity.

### Flexible Billing Model

DR Automation for PowerVS follows a usage-based billing model, with flexible options based on the selected resources and configurations. The IBM Cloud Service Framework supports accurate billing and comprehensive reporting, ensuring customers have clear visibility into DR-related costs.

---

## IBM Cloud Service Framework


The **IBM Cloud Service Framework** enhances DR Automation for PowerVS by enabling seamless service deployment and management. Key components include:

- **Service Broker**: Manages compute, storage, and network resources, allowing users to select DR services from the IBM Cloud Catalog and configure deployment details. This component plays a central role in streamlining and automating DR processes.

- **Resource Management Controller (RMC)**: Automates provisioning, image import, and VM configuration, making DR deployment efficient and straightforward for users.

- **Orchestrator (KSYS)**: Coordinates DR workflows and ensures that VMs recover in a defined sequence, minimizing downtime and data loss.

- **Security and Compliance**: Ensures a secure, compliant environment through robust controls and monitoring. This includes IBM Cloud services like Activity Tracker (for monitoring) Cloud Object Storage (COS) (for secure storage), and Key Management (for data security).

- **Reliable Connectivity**: Maintains continuous, secure access to DR resources through redundant network connections, enhancing reliability and resilience.

This integrated framework provides a secure, compliant, and efficient DR solution that aligns closely with the high-level architecture for DR Automation in IBM data centers.

---

## Hardware Specifications

IBM Power servers supported by DR Automation for PowerVS include:

- **IBM Power S922** (9009-22A)
- **IBM Power S922** (9009-22G)
- **IBM Power E980** (9080-M9S)
- **IBM Power E1080** (9080-HEX)

For more details, refer to the specific data sheets and hardware overview table.

---

## Supported Storage Tiers

DR Automation for PowerVS offers storage with configurable IOPS levels to meet diverse DR requirements:

| Tier Level | IOPS       | Performance                                |
|------------|------------|--------------------------------------------|
| **Tier 0** | 25 IOPS/GB | High performance for critical workloads    |
| **Tier 1** | 10 IOPS/GB | Balanced performance for general workloads |
| **Tier 3** | 3 IOPS/GB  | Cost-effective for non-critical applications |

With the IBM Cloud Service Framework, storage is allocated based on deployment needs, ensuring efficient usage of resources and seamless management.

---

## Network Configurations

### Public Network

DR Automation for PowerVS offers public network connectivity for seamless access and configuration. IBM configures the network environment for secure public connections, including firewall protection and support for SSH, HTTPS, and IBM i terminal emulation.

### Private Network

A private network setup is recommended for secure communication between PowerVS instances in primary and DR sites. This configuration supports:

- **IBM Cloud Resources Access**:
Enable access to IBM Cloud Bare Metal Servers, Kubernetes containers, and Cloud Object Storage.

- **Direct Link Connect**:
Use Direct Link Connect for secure, low-latency communication between DR environments.

---

## Setting Up DR Automation

1. **Create IBM Cloud Account**: Log in to your IBM Cloud account.
2. **Access DR Automation in IBM Catalog**: Locate the DR Automation for PowerVS tile.
3. **Configure Resources**: Set up storage, compute, and network resources according to DR needs.
4. **Monitor and Test**: Schedule DR tests and monitor system health.

---

This document reflects the integration of the IBM Cloud Service Framework in DR Automation for PowerVS, ensuring seamless deployment, secure management, and a smooth user experience. Let me know if any additional customization is needed.
