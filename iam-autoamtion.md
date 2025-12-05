---
copyright:
  years: 2025
lastupdated: "2025-12-05"

subcollection: dr-automation-powervs

keywords: iam

---

# Managing identity and access management (IAM)
{: #iam-manage}

IAM enables you to securely authenticate users, control access to Power® Virtual Server resources with resource groups, and allow access to specific resources for a set of users with access groups. IAM is your one-stop shop for all user and resource management in the IBM Cloud.
{:shortdesc: .shortdesc}

For more information about IAM, review the following information:

- [Getting started with IAM](https://cloud.ibm.com/docs/account?topic=account-access-getstarted)
- [Managing resource groups](https://cloud.ibm.com/docs/account?topic=account-rgs)
- [Setting up access groups](https://cloud.ibm.com/docs/account?topic=account-groups&interface=ui)
- [IAM concepts](https://cloud.ibm.com/docs/account?topic=account-iamoverview)

## Platform access roles
{: #par}

You can use platform access roles to enable users to complete tasks on IBM Cloud resources, such as creating users or adding services.

The following table displays the IAM platform access roles and the corresponding type of control that is allowed by the DR Automation for powerVS:

## IAM platform access roles
{: #iam-par-acc-role}

| Platform access role | Type of access allowed                                                                                   |
|----------------------|----------------------------------------------------------------------------------------------------------|
| Viewer               | View instances and list instances.                                                                       |
| Operator             | View instances and manage aliases, bindings (IBM Power Virtual Server (On-premises) only), and credentials. |
| Editor               | View instances, list instances, create instances, and delete instances.                                  |
| Administrator        | View instances, list instances, create instances, delete instances, and assign policies to other users.   |
{: caption="IAM platform access roles" caption-side="bottom"}

### Service access roles
{: #ser-acc-ro}

You can use the service access roles to define the actions that the users can perform on Power Virtual Server resources. The following table displays the IAM service access roles and the corresponding actions that a user can complete by using the Dr Automation for PowerVS:

## IAM service access roles
{: #ser-acc-role}

| Service access role | Description of actions                                                                                                                  |
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Reader              | View all resources (such as SSH keys, storage volumes, and network settings). You cannot make changes to the resources.                |
| Manager             | Configure all resources. You can perform the following actions:                                   |
|                     | - Create instances                                                                                                                      |
|                     | - Increase storage volume sizes                                                                                                         |
|                     | - Create SSH keys                                                                                                                       |
|                     | - Modify network settings                                                                                                               |
|                     | - Create boot images                                                                                                                    |
|                     | - Delete storage volumes |
{: caption="IAM service access roles" caption-side="bottom"}

To see the complete list of actions for each specific role, see the [IAM roles and actions page](https://cloud.ibm.com/docs/account?topic=account-iam-service-roles-actions#power-iaas-roles) in IBM Cloud documentation.

### Access role requirements for {{site.data.keyword.DR_full_notm}}
{: #ser-acc-role-dr-auto}


{{site.data.keyword.DR_full_notm}} requires additional access to various network and infrastructure features to ensure seamless failover, recovery, and redundancy. These access roles are determined by the specific recovery and network requirements of your DR solution. For instance, setting up redundancy for storage replication or configuring network routes during failover may require access to services like VPC, Transit Gateway, or Cloud Object Storage.

The following table outlines the additional access roles required for DR automation, along with the corresponding resources and attributes for API key:

### Resources and attributes
{: #res-atri}

| **Additional Access Roles**         | **Resources and Attributes**                    |
|-------------------------------------|------------------------------------------------|
| **Editor, Manager**                 | Power Virtual Server DR Automation             |
| **Editor, Manager**                 | Power Virtual Server service                   |
| **Reader, Viewer**                  | VPC Infrastructure Services service            |
| **Manager**                         | Transit Gateway service                        |
| **Reader, Viewer**                  | All resources in account (including future IAM-enabled services) |
| **Viewer**                          | All resource groups                            |
| **Manager**                         | Cloud Object Storage                           |
| **Manager**                         | Schematics                                     |
| **Reader, Viewer**                  | Secret Manager                                 |
{: caption="Additional access roles" caption-side="bottom"}


### User access scenarios

For more information about managing and assigning access by using IAM policies, see [Managing access to resources](https://cloud.ibm.com/docs/account?topic=account-iamusermanpol).
