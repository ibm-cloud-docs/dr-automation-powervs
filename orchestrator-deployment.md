---
copyright:
  years: 2025
lastupdated: "2025-01-16"

subcollection: dr-automation

keywords: orch dep

---

# Orchestrator deployment
{: #orch}

The Disaster Recovery (DR) orchestrator is successfully deployed in IBM Cloud Power Virtual Server (PowerVS). The **Orchestrator Details** and **Service Details** sections provide comprehensive technical insights that help administrators and cloud engineers monitor and manage disaster recovery automation for their infrastructure. Each element within these sections offers critical operational information, ensuring that the DR setup is correctly configured and ready for failover scenarios.
{:shortdesc: .shortdesc}

## Orchestrator details
{: #orc-det}

This section highlights the orchestrator's operational status and key identifiers:

- The unique identifier for the orchestrator instance responsible for managing failover, failback, and replication processes between the primary and DR sites.
  
- Displays the current health and state of the orchestrator, such as "Running." The orchestrator must be operational for DR functions to be ready.

- Refers to the secure IBM Cloud SSH key used for authenticated and encrypted communication between the orchestrator and the managed VMs involved in DR.

- Indicates the SSH key linked to the orchestrator for remote access to VMs. Proper configuration is crucial for secure VM operations.

- The Infrastructure as Code (IaC) environment that automates the provisioning of DR resources, leveraging Terraform templates to define workflows for automation.

- Shows whether the orchestrator is successfully connected to the Schematics workspace. A “Running” status indicates successful infrastructure automation.

## Service details
{: #service-det}

The Service Details section provides a comprehensive overview of the disaster recovery (DR) service setup within IBM Cloud PowerVS, ensuring that the correct infrastructure is in place to support high availability and business continuity in the event of a disaster. It includes:

- Identifies the DR service configured in IBM Cloud for the orchestrator, linking it to the correct DR environment.

- Specifies the region or data center, such as "Dallas 12," where the DR resources are hosted and where failover will occur.

- Displays the IBM Cloud resource group managing the DR resources, allowing for resource-level permissions and management.

- A globally unique identifier for the DR service within IBM Cloud, enabling resource tracking and auditing across cloud environments using APIs.


By following this deployment and monitoring process, administrators and engineers can be confident that the disaster recovery setup within IBM Cloud PowerVS is robust, reliable, and ready to ensure business continuity in case of unforeseen events.
