---
front_matter_title: "Support Center"
lastupdated: "2024-10-26"
copyright: "2023, 2024"
subcollection: dr-automation
---
# Troubleshooting


## How can the user rotate the API key?

Rotating the API key ensures secure access to the service. It is a straightforward process that can be done via the GUI interface.

To rotate the API key, follow these steps:

1. Access the VM Recovery Manager DR GUI.
2. Navigate to the Policies tab from the top navigation bar.
3. Locate the API Key field in the list of tunable attributes.
4. Click Regenerate to create a new API key.
5. Save the changes to apply the new key securely.

This process ensures the security of API interactions with the system.

## How does the service work?

The service automates disaster recovery processes, enabling efficient failover and failback operations. Its architecture leverages key components to ensure seamless functionality during recovery scenarios.

Here’s how it works:

1. Orchestrates disaster recovery by automating failover and failback processes across sites.
2. The Service Broker manages resource provisioning and billing.
3. The KSYS (DR Orchestrator) handles VM orchestration, ensuring resources are brought online in the correct sequence during recovery.
4. Data replication between primary and backup sites is facilitated by Global Replication Services (GRS), ensuring consistency and resilience.
5. Users configure and monitor the DR environment via the IBM Cloud GUI and manage VMs through the VM Recovery Manager HA/DR interface.

With its robust features, the solution simplifies disaster recovery, providing businesses with a reliable and efficient option.

## What access does the user need?

To use the service effectively, users need specific IAM roles and permissions, along with access to certain infrastructure services.

Follow these steps to ensure the correct access is assigned:

### IAM roles for access

- Platform roles:
  - Viewer: View instances and list resources.
  - Operator: Manage aliases and bindings.
  - Editor: Create and delete instances.
  - Administrator: Assign policies to other users.
- Service roles:
  - Reader: View resources like SSH keys and network settings.
  - Manager: Configure resources, including creating instances, increasing storage, and modifying settings.

### Additional access

- Direct Link Service: For network redundancy during failover.
- Transit Gateway: For routing traffic between recovery environments.
- VPC Services: For secure network management and configuration.

Ensuring the correct roles and access enables seamless use of the service, supporting efficient disaster recovery operations.
