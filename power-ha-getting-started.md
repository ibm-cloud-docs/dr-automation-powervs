---

copyright:
  years: 2025
lastupdated: "2026-04-16"

subcollection: dr-automation-powervs

keywords: powerha, Power HA, getting started

---

---

{{site.data.keyword.attribute-definition-list}}

# Getting started with PowerHA Automation for Power Virtual Server

{: #getting-started}
{: toc-content-type="tutorial"}
{: toc-services=""}
{: toc-completion-time="10m"}


Setup {{site.data.keyword.DR_full}} **PowerHA** helps you deploy and operate high-availability clusters by using PowerHA SystemMirror with minimal manual effort. The service integrates with IBM Cloud to streamline onboarding, cluster lifecycle operations, and service management for PowerHA-enabled virtual machines.

You can deploy PowerHA from the IBM Cloud catalog. The UI catalog guides you through selecting the PowerHA plan and associating existing PowerVS virtual machines that participate in a PowerHA cluster. The service focuses on automation, visibility, and lifecycle management, while cluster configuration and application setup remain customer-managed.
{: shortdesc}


## Before you begin
{: #prereqs}

Before you deploy HA automation, ensure that the following requirements are met:

1. **IBM Cloud account**: You must have an active IBM Cloud account. If required, sign up at [Sign up for IBM Cloud](https://cloud.ibm.com/registration).

2. **IAM access** : Configure the required Identity and Access Management (IAM) roles and permissions for PowerHA.  
For more information, see [Managing PowerHA IAM access](/docs/dr-automation-powervs?topic=dr-automation-powervs-iam-manage).

3. **API key** : An IBM Cloud API key is required for service provisioning and ongoing operations.


## Lifecycle of PowerHA
{: #lpvsdrauto}

![PowerHA life Cycle](images/Power-ha-suits-flow-diagram.svg "PowerHA life Cycle"){: caption="HA Automation life Cycle" caption-side="bottom"}


## Next steps
{: #next-steps}

After provisioning PowerHA, you can:

1. Validate the API key and select the High availability location and Power Virtual Server workspace from the available list.

2. Add the node and download the agent.

HA cluster administration, application resource groups, and failover policies continue to be managed by using PowerHA SystemMirror tools.

These advanced configurations help you optimize your disaster recovery setup for business resilience.
