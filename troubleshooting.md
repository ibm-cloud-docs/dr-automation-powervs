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

## How can the user resolve the issue of no BSS events being called from the service?

Troubleshooting the lack of BSS events involves verifying the service’s configuration and connectivity. Follow these steps:

1. Access the {{site.data.keyword.DR_short}} GUI.
2. Navigate to the Configuration tab to review the Service Broker settings.
3. Check the Billing and Subscription System (BSS) API connectivity under the Network Diagnostics section.
4. Verify the API key and credentials in the Service Configuration panel.
5. Run a test provision operation to confirm BSS integration.

This process ensures that the system triggers and captures BSS events accurately.

## How can the user resolve the issue of no IAM actions being performed from the service?

To troubleshoot the lack of IAM actions, ensure the appropriate permissions and configurations are in place. Follow these steps:

1. Log in to the IAM Console via the IBM Cloud portal.
2. Review the access roles assigned to the DR automation service under the Access Groups tab.
3. Enable Activity Tracker to monitor IAM events by navigating to the Monitoring tab.
4. Simulate an IAM action, such as granting a permission, and check the Activity Tracker logs for corresponding entries.
5. If authentication issues persist, rotate the API key by following the steps in the Policies tab of the GUI.

This process guarantees that IAM actions are properly configured and logged for security and auditing purposes.

## How can you resolve the "Error getting access token" during the provisioning of the disaster recovery service?

The error occurs when the service fails to retrieve the necessary access token for authentication. To resolve this issue, follow these steps:

1. Access the {{site.data.keyword.DR_short}} GUI.
2. Navigate to the Policies tab in the top navigation bar.
3. Check the API key field and ensure that the key is valid and not expired.
4. Regenerate the API key by clicking the Regenerate button, then save the changes to update the system with the new key.
5. Verify IAM roles and permissions for the DR automation service to ensure sufficient access to generate tokens.
6. Retry the provisioning operation and monitor the logs to confirm a successful outcome.

This process ensures secure and proper authentication for provisioning operations, resolving the token access issue.

## How can you resolve the "orchestrator password format is incorrect" error during the update of the disaster recovery service?

This error occurs when the password provided for the orchestrator does not meet the required format. To resolve this issue, follow these steps:

1. Access the {{site.data.keyword.DR_short}} GUI.
2. Navigate to the Policies tab in the top navigation bar.
3. Locate the Orchestrator Password field under the tunable attributes section.
4. Ensure that the password meets the required format, which typically includes:
    - At least 8 characters.
    - A mix of uppercase and lowercase letters.
    - At least one number and one special character (e.g., @, #, $).
5. Update the password to meet the format requirements and save the changes.
6. Retry the update operation and verify that the error is resolved.

This process ensures the password complies with security standards and allows the update to proceed successfully.

## How can you resolve the "delete provision disaster-recovery-service -failure" error?

This error occurs when the system fails to delete the provisioned disaster recovery service due to an unassigned error. To resolve this issue, follow these steps:

1. Access the {{site.data.keyword.DR_short}} GUI.
2. Navigate to the Events tab and review the detailed logs to identify any additional context or clues about the failure.
3. Verify API connectivity by running a test command (e.g., ping or curl) to ensure the service can communicate with required endpoints.
4. Check for active resources associated with the provisioned service. Ensure that no dependencies (e.g., VMs, storage volumes) are preventing deletion.
5. Reset the API key by navigating to the Policies tab and regenerating the key if token-related errors are suspected.
6. Retry the delete operation via the GUI or API and monitor for any changes in the outcome.

This process helps identify and resolve underlying issues, ensuring the successful deletion of the provisioned disaster recovery service.
