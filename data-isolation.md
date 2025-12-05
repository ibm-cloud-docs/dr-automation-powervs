---
copyright:
  years: 2025
lastupdated: "2025-11-21"

subcollection: dr-automation-powervs

keywords: data isolation

---

# Data Isolation
{: #di}

## Overview
{: #ovr}

Data isolation in IBM Cloud is essential for protecting customer data in multi-tenant cloud environments, especially for {{site.data.keyword.DR_full}}. IBM Cloud offers a suite of tools and services that ensure data remains segregated, secure, and compliant with regulatory standards. This document details key strategies and components that work together to provide robust data isolation within the {{site.data.keyword.DR_full_notm}} framework.
{:shortdesc: .shortdesc}

## Key data isolation strategies
{: #keydata}

### Virtual Private Cloud
{: #vpc}

IBM Cloud’s Virtual Private Cloud (VPC) provides an isolated network environment for managing {{site.data.keyword.DR_short}} resources securely. It enables you to control IP address ranges, subnets, routing, and access, ensuring that DR resources are isolated from other IBM Cloud customers.

- **Private IP Addressing**: Resources receive private IP addresses, making them accessible only within the VPC or through configured access.

- **Subnets**: Organize resources into public or private subnets, further isolating sensitive DR applications.

- **Peering and VPN Connections**: VPC peering and VPNs secure connections across on-premises and cloud environments, maintaining data isolation.

### Dedicated Cloud and Private Infrastructure
{: #de-pr-infra}

IBM Cloud offers **dedicated cloud** options for exclusive access to physical servers, ideal for {{site.data.keyword.DR_short}}’s sensitive workloads.

- **IBM Cloud Dedicated** provides physical isolation, ensuring no shared infrastructure with other tenants.
- **IBM Cloud Bare Metal Servers** and **Virtual Servers** deliver single-tenant environments, enhancing data isolation by controlling compute resources directly.

### Data Encryption
{: #da-en}

Data encryption ensures that sensitive DR data is secure and isolated.

- **Encryption at Rest**: Data is encrypted by default with AES-256, securing storage in IBM Cloud services.
- **Encryption in Transit**: Transport Layer Security (TLS) protects data during transmission.
- **IBM Key Protect**: Centralized key management for encryption keys, supporting Bring Your Own Key (BYOK) capabilities, is essential for DR data replication and storage.

### Identity and access management
{: #de-pr-acces}

**IBM Cloud IAM** provides role-based access control for DR resources, ensuring that only authorized users and systems can access critical DR functions.

- **Role-Based Access Control (RBAC)**: Controls access to specific DR resources by defining roles and permissions.

### Cloud Object Storage for bucket level isolation
{: #de-pr-infra-bucket}

**IBM Cloud Object Storage** is used for storing DR backups, logs, and replication snapshots, providing bucket-level data isolation.

- **Bucket-Level Access Control**: IAM policies control read and write access to individual buckets, isolating sensitive data.
- **Bucket Encryption**: Data is encrypted by default at rest, with options for customer-managed keys via IBM Key Protect.

### Network Security and Isolation
{: #de-pr-iso}

IBM Cloud offers network isolation and security features for DR resources.

- **Security Groups**: Act as virtual firewalls, managing traffic flow within VPCs.
- **Network ACLs**: Control inbound and outbound traffic at the subnet level.
- **Private Endpoints and VPNs**: Facilitate isolated communication between IBM Cloud services, maintaining data privacy.

### Compliance and Data Residency
{: #de-pr-da-ta-re}

IBM Cloud’s compliance tools and certifications help meet regional and regulatory requirements for DR data isolation.

- **Data Residency**: Allows data to be stored in specific geographic regions to comply with regulations.
- **Compliance Certifications**: IBM Cloud is certified for standards like ISO 27001, SOC 2, and PCI-DSS.

## {{site.data.keyword.DR_short}}-Specific Data Isolation Components

### KSYS (DR Orchestrator)
{: #orch}

The **KSYS** orchestrates disaster recovery operations, coordinating failover and failback across sites, ensuring that virtual machines and resources are synchronized and recovered securely. KSYS enforces isolation by managing access and operations at both source and target sites, preserving data integrity during DR events.

### DR Service Broker
{: #drsb}

The **DR Service Broker** provides a centralized interface for managing DR services across PowerVS instances. It allows streamlined access to DR resources, configurations, and policies while maintaining isolated operations for each customer environment.

### Control Plane
{: #cp}

The **Control Plane** manages {{site.data.keyword.DR_short}} operations within PowerVS, handling resource monitoring, API requests, and synchronization across sites. It ensures isolated DR processes by controlling data flow and access between primary and secondary sites.

### Replication Services
{: #rs}

**Replication Services** manage policy-based replication of data between sites, ensuring data consistency for DR. Isolation is maintained by controlling data transfer policies, synchronizing only the required data, and securing it across network boundaries.

### VM Recovery Manager Agents
{: #vmrma}

The **VM Recovery Manager Agents** are installed on nodes to manage site-level and VM-level DR tasks, including resource monitoring and event logging. They contribute to data isolation by performing dedicated DR orchestration functions within isolated environments.

### IBM Cloud Monitoring
{: #ibmcm}

**IBM Cloud Monitoring** tracks the health and performance of DR resources, monitoring key metrics related to DR readiness and synchronization. Monitoring enhances data isolation by identifying potential vulnerabilities or unauthorized access to DR resources.

### Code Engine
{: #ce}

IBM’s **Code Engine** is used for job scheduling and executing DR tasks based on events or schedules. Code Engine supports event-driven execution, allowing DR processes to be triggered automatically in response to specific conditions, ensuring timely and isolated DR operations.

### IBM Cloud Container Registry (ICR)
{: #icr}

The **IBM Cloud Container Registry** (ICR) manages container images essential for DR workloads. It ensures that recovery images are consistently accessible in isolated environments, with vulnerability scanning for security assurance.

## Monitoring and Logging
{: #mal}

IBM Cloud’s monitoring and logging services enhance data isolation by capturing detailed records of access and events.

- **IBM Cloud Monitoring**: Tracks DR operations and flags unusual activities that could indicate potential security issues.
- **IBM Cloud Logging**: Logs access events, detailing which user or service accessed specific DR data, ensuring auditability.

## Best Practices for Data Isolation
{: #bpdi}

- **Use VPCs for Network Isolation**: VPCs provide isolated networks essential for data security in DR.
- **Implement Robust IAM Policies**: Apply IAM to enforce role-based access, limiting who can access DR resources.
- **Encrypt Data at Rest and in Transit**: Both encryption types are essential for protecting DR data.
- **Use Private Endpoints and VPNs**: To ensure isolated communication between DR resources and sites.
- **Select Appropriate Regions for Data Residency**: Align data storage with regulatory requirements for data residency.

IBM Cloud’s data isolation strategies for {{site.data.keyword.DR_short}} in PowerVS ensure that customer data is protected, compliant, and ready for recovery in secure environments. By leveraging dedicated infrastructure, IAM, VPC, and encryption, IBM Cloud provides a robust environment for disaster recovery, preserving data isolation at every stage.
