---

copyright:
  years: 2025
lastupdated: "2026-02-23"

subcollection: dr-automation-powervs

keywords: powerha, Power HA, getting started

---

---

{{site.data.keyword.attribute-definition-list}}

# Getting started with HA Automation for Power Virtual Server

{: #getting-started}
{: toc-content-type="tutorial"}
{: toc-services=""}
{: toc-completion-time="10m"}


Setup HA Automation of {{site.data.keyword.DR_full}} helps you deploy and operate high-availability clusters using PowerHA SystemMirror with minimal manual effort. The service integrates with IBM Cloud to streamline onboarding, cluster lifecycle operations, and service management for PowerHA-enabled virtual machines.

You can deploy PowerHA automation from the IBM Cloud catalog. The catalog UI guides you through selecting the PowerHA plan and associating existing PowerVS virtual machines that participate in a PowerHA cluster. The service focuses on automation, visibility, and lifecycle management, while cluster configuration and application setup remain customer-managed.
{: shortdesc}


## Before you begin
{: #prereqs}

Before you deploy PowerHA automation, ensure that the following requirements are met:

1. **IBM Cloud account**  
   You must have an active IBM Cloud account. If required, sign up at https://cloud.ibm.com/registration.

2. **IAM access**  
   Configure the required Identity and Access Management (IAM) roles and permissions for PowerHA automation.  
   For more information, see [Managing PowerHA automation IAM access](/docs/dr-automation-powervs?topic=dr-automation-powervs-iam-manage).

3. **PowerVS environment**  
   Ensure that your Power Virtual Server workspaces and virtual machines are already created and accessible.

4. **PowerHA prerequisites**  
   PowerHA SystemMirror must be installed or planned for installation on the selected PowerVS virtual machines. Cluster creation and application configuration are performed outside the automation service.

5. **API key**  
   An IBM Cloud API key is required for service provisioning and ongoing operations.


## Lifecycle of {{site.data.keyword.DR_full_notm}}
{: #lpvsdrauto} 

![{{site.data.keyword.DR_full_notm}} life Cycle](images/Power-ha-suits%20flow-diagram-Page-1.drawio.svg "{{site.data.keyword.DR_full_notm}} life Cycle"){: caption="Power Virtual Server HA DR Suits life Cycle" caption-side="bottom"}



## Next steps
{: #next-steps}

After deploying PowerHA automation, you can:

- View the status of the PowerHA automation service
- Associate and manage PowerVS virtual machines
- Monitor operational state through the IBM Cloud console

PowerHA cluster administration, application resource groups, and failover policies continue to be managed using PowerHA SystemMirror tools.

These advanced configurations help you optimize your disaster recovery setup for business resilience.
