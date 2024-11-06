---
front_matter_title: "Data isolation"
lastupdated: "2024-10-23"
copyright: "2023, 2024"
subcollection: dr-automation
---
# Data isolation

## Architecture Overview

The overview includes key services and components of the IBM DR automation for PowerVS architecture. Here's a recap of the main services mentioned:

## Key DR Automation Services and Components

- **KSYS (DR Orchestrator)**: Manages the disaster recovery orchestration, coordinating failover and failback operations across sites. KSYS ensures that VMs and associated resources are properly synchronized and recovered in a DR event.

- **DR Service Broker**: Provides a centralized interface for managing DR services across PowerVS instances, enabling streamlined access to resources and configurations required for disaster recovery.

- **Control Plane**: Manages DR automation operations within PowerVS, handling critical functions such as resource monitoring, API requests, and synchronization between sites to ensure seamless DR processes.

- **Replication Services**: Manages policy-based replication of data between primary and secondary sites, ensuring data consistency and availability for DR scenarios.

- **IBM Cloud Identity and Access Management (IAM)**: Provides authentication and authorization for DR automation activities, managing access to critical DR resources.

- **VM Recovery Manager Agents**: Installed on nodes to perform site-level and VM-level DR tasks, including resource monitoring and event logging for DR orchestration.

- **IBM Cloud Object Storage**: Stores backups and logs, including DR event logs and replication snapshots, providing reliable storage for DR data.

- **IBM Key Protect**: Manages encryption keys for DR data replication, ensuring that data remains secure throughout the DR lifecycle.

- **IBM Cloud Monitoring**: Tracks the health and performance of DR resources, monitoring key metrics for DR readiness and ongoing synchronization. These components work together to provide a resilient, secure, and automated environment for disaster recovery, enabling quick and reliable failover and failback processes within PowerVS.

- **Code Engine**: Job scheduling executes DR tasks based on schedules or events, automating workflows critical for DR readiness and recovery. Event-driven execution triggers DR processes automatically, ensuring timely response in failover scenarios. Integrated security leverages IBM Cloud IAM to authenticate and control access, securing DR operations.

- **IBM Cloud Container Registry (ICR)**: Manages container images essential for DR workloads, ensuring consistent access to recovery images. Vulnerability scanning monitors.
