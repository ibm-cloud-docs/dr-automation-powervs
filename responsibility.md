---
front_matter_title: "Responsibilities"
lastupdated: "2024-10-23"
copyright: "2023, 2024"
subcollection: dr-automation
---
# Understanding your responsibilities when you use DR Automation for PowerVS

Learn about the management responsibilities and terms and conditions that you have when you use DR Automation for PowerVS deployable architecture.

- For more information about the responsibilities for you and for IBM® when you use a deployable architecture, see [Understanding your responsibilities when you use deployable architectures](https://cloud.ibm.com/docs/overview?topic=overview-shared-responsibilities#managed-offerings-on-customers-resources-responsibilities).
- For a high-level view of the service types in IBM Cloud® and the breakdown of responsibilities between the customer and IBM for each type, see [Shared responsibilities for using IBM Cloud® products](https://cloud.ibm.com/docs/overview?topic=overview-shared-responsibilities).
- For the overall terms of use, see [IBM Cloud Terms and Notices](https://cloud.ibm.com/docs/overview?topic=overview-terms).
- For more information about the shared responsibilities for each Financial Services Validated service, see [Responsibilities for operating services in your deployment in IBM Cloud Framework for Financial Services](https://cloud.ibm.com/docs/overview?topic=overview-financial-services-validated-services).

Review the following sections for the specific responsibilities for you and for IBM when you use DR Automation for PowerVS.

## Incident and Operations Management

Incident and operations management includes tasks such as monitoring, event management, high availability, problem determination, recovery, and full state backup and recovery.

The DR Automation for PowerVS deployable architectures do not identify specific responsibilities in this area.

## Identity and Access Management

Identity and access management includes tasks such as authentication, authorization, access control policies, and approving, granting, and revoking access.

| Task | IBM Responsibilities | Your Responsibilities |
|------|-----------------------|-----------------------|
| **Secure with least privilege** | Document the minimal IAM access requirements to run the deployable architecture. | |
| **Manage secrets** | | Generate necessary secrets (e.g., IAM API keys, SSH keys) required for the deployable architecture and manage them following secure best practices. |
_Table 1: Responsibilities for identity and access management_

## Security and Regulation Compliance

Security and regulation compliance includes tasks such as security controls implementation and compliance certification.

| Task | IBM Responsibilities | Your Responsibilities |
|------|-----------------------|-----------------------|
| **Meet security and compliance objectives** | Provide a deployable architecture that complies with the predefined set of controls. These controls may not cover the entire IBM Cloud Framework for Financial Services profile. | |
| **Verify configuration changes** | | Understand the impact of user-initiated changes on security and compliance, and run IBM Cloud Security and Compliance Center checks if necessary. |
| **Ensure that the operating system image does not contain vulnerabilities** | IBM provides verified OS images, updates them post-deployment, and uses RHEL repositories for additional components. | Ensure the OS remains secure and compliant after deployment. |
_Table 2: Responsibilities for security and regulation compliance_

## Disaster Recovery

Disaster recovery encompasses tasks such as establishing DR sites, configuring backup environments, data replication, and failover management during disaster events.

The DR Automation for PowerVS deployable architectures do not identify specific responsibilities in this area.
