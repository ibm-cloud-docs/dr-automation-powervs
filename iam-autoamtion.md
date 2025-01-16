---
copyright:
  years: 2025
lastupdated: "2025-01-16"

subcollection: dr-automation

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

The following table displays the IAM platform access roles and the corresponding type of control that is allowed by the DR Autoamtion for powerVS:

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

You can use the service access roles to define the actions that the users can perform on Power Virtual Server resources. The following table displays the IAM service access roles and the corresponding actions that a user can complete by using the Dr Autaomtion for PowerVS:

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

#### Access role requirements for DR Automation for PowerVS
{: #ser-acc-role-dr-auto}


DR automation for PowerVS requires additional access for certain network and infrastructure features, including Direct Link, Transit Gateway, and Virtual Private Cloud (VPC) services. These access roles may be needed depending on the recovery and network requirements of your DR solution. For example, configuring network redundancy during failover might require access to Direct Link services.

The following table lists the additional access roles required for DR automation for PowerVS, along with the corresponding services:

## Additional access roles for DR automation for PowerVS
{: #add-ser-acc-ro}

| Additional access role                     | Resource attributes for DR automation                                                                           |
|--------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| Editor, Manager, Operator, Reader, Viewer  | DR automation for PowerVS service                                                                               |
| Editor, Manager, Operator, Reader, Viewer, VPN Client | VPC Infrastructure Services for network management and configuration                                 |
| Editor, Operator, Viewer                   | Transit Gateway service for routing traffic between recovery environments                                        |
| Reader, Viewer                             | All resources within the account (including future IAM-enabled services that may be needed for DR)              |
| Editor, Operator, Viewer                   | Direct Link service for establishing connections between on-premises and DR sites                               |
| Viewer                                     | All resource groups for basic monitoring and visibility across resources                                        |
| Viewer                                     | Satellite service On-premises for managing hybrid cloud resources within DR scenarios                           |
{: caption="Additional access roles for DR automation for PowerVS" caption-side="bottom"}


### User access scenarios

For more information about managing and assigning access by using IAM policies, see [Managing access to resources](https://cloud.ibm.com/docs/account?topic=account-iamusermanpol).
