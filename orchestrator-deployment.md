---
front_matter_title: "Orchestrator deployment"
lastupdated: "2024-10-26"
copyright: "2023, 2024"
subcollection: dr-automation
---

# Orchestrator deployment

The Disaster Recovery (DR) orchestrator is successfully deployed in IBM Cloud Power Virtual Server (PowerVS). The **Orchestrator Details** and **Service Details** sections provide comprehensive technical insights that help administrators and cloud engineers monitor and manage disaster recovery automation for their infrastructure. Each element within these sections offers critical operational information, ensuring that the DR setup is correctly configured and ready for failover scenarios.

## Orchestrator Details

This section highlights the orchestrator's operational status and key identifiers:

- **Orchestrator Name**: The unique identifier for the orchestrator instance responsible for managing failover, failback, and replication processes between the primary and DR sites.
  
- **Orchestrator Status**: Displays the current health and state of the orchestrator, such as "Running." The orchestrator must be operational for DR functions to be ready.

- **IBM Cloud SSH Key Secret**: Refers to the secure IBM Cloud SSH key used for authenticated and encrypted communication between the orchestrator and the managed VMs involved in DR.

- **SSH Key Name**: Indicates the SSH key linked to the orchestrator for remote access to VMs. Proper configuration is crucial for secure VM operations.

- **Schematics Workspace**: The Infrastructure as Code (IaC) environment that automates the provisioning of DR resources, leveraging Terraform templates to define workflows for automation.

- **Schematics Workspace Connection Status**: Shows whether the orchestrator is successfully connected to the Schematics workspace. A “Running” status indicates successful infrastructure automation.

## Service Details

The **Service Details** section provides a comprehensive overview of the disaster recovery (DR) service setup within IBM Cloud PowerVS, ensuring that the correct infrastructure is in place to support high availability and business continuity in the event of a disaster. It includes:

- **Service Name**: Identifies the DR service configured in IBM Cloud for the orchestrator, linking it to the correct DR environment.

- **Disaster Recovery Location**: Specifies the region or data center, such as "Dallas 12," where the DR resources are hosted and where failover will occur.

- **Resource Group**: Displays the IBM Cloud resource group managing the DR resources, allowing for resource-level permissions and management.

- **CRN (Cloud Resource Name)**: A globally unique identifier for the DR service within IBM Cloud, enabling resource tracking and auditing across cloud environments using APIs.

---

By following this deployment and monitoring process, administrators and engineers can be confident that the disaster recovery setup within IBM Cloud PowerVS is robust, reliable, and ready to ensure business continuity in case of unforeseen events.
