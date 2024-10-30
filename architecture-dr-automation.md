---
front_matter_title: "DR Automation for PowerVS Architecture"
lastupdated: "2024-10-23"
copyright: "2023, 2024"
subcollection: dr-automation
---
# DR Automation for PowerVS Architecture Overview

IBM® DR Automation for PowerVS is a robust disaster recovery solution integrated within IBM’s data centers, distinct from general IBM Cloud resources. It offers dedicated network configurations and direct-attached storage to ensure secure and reliable DR capabilities.

The **IBM Cloud Service Framework** enables seamless deployment and management of DR Automation for PowerVS by integrating essential components such as the **IBM Cloud Service Broker**, **Resource Management Controller (RMC)**, and the **IBM Cloud Catalog**. This framework simplifies the DR setup process, enhances security, and ensures compliance, delivering a reliable DR solution within the IBM Cloud environment.

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

The DR Automation for PowerVS system is hosted in IBM data centers, separate from the IBM Cloud environment, with isolated networks and dedicated storage solutions. With this system, users can automate disaster recovery (DR) processes, ensuring fast and reliable recovery of workloads in the event of failures.

The **IBM Cloud Service Framework** plays a central role in DR Automation for PowerVS, enabling customers to select DR services from the IBM Cloud Catalog and provide deployment details. The **Resource Management Controller (RMC)** manages provisioning, image import, and VM configuration, while maintaining security and compliance through stringent controls. This architecture also includes components such as **Activity Tracker**, **Cloud Object Storage**, and **Key Management** to enhance security, auditability, and resilience.

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

The IBM Cloud Service Framework provides a streamlined experience, with the **IBM Cloud Service Broker** allowing users to choose services from the catalog and specify deployment parameters. The **Resource Management Controller (RMC)** automates provisioning tasks and VM configurations for DR, ensuring a smooth and intuitive user experience. Additional IBM Cloud services, like **Activity Tracker**, **Cloud Object Storage**, and **Key Management**, provide a secure and compliant environment, with reliable connectivity through redundant network connections.

### Flexible Billing Model

DR Automation for PowerVS follows a usage-based billing model, with flexible options based on the selected resources and configurations. The IBM Cloud Service Framework supports accurate billing and comprehensive reporting, ensuring customers have clear visibility into DR-related costs.

---

## IBM Cloud Service Framework

The IBM Cloud Service Framework enhances DR Automation for PowerVS by enabling seamless service deployment and management. Key components include:

- **IBM Cloud Service Broker**:
Select services from the IBM Cloud Catalog and configure DR deployment details.

- **Resource Management Controller (RMC)**:
Handles VM provisioning, image import, and configuration, making DR deployment efficient and straightforward.
- **Security and Compliance**:
Ensures compliance through robust controls, monitoring, and IBM Cloud security services.

- **Reliable Connectivity**: Leverages redundant network connections to maintain continuous, secure access to DR resources.

This integrated framework leverages IBM Cloud services like **Activity Tracker** (for monitoring), **Cloud Object Storage** (for secure storage), and **Key Management** (for data security), providing a secure, compliant, and efficient DR solution.

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
