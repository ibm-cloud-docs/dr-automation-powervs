---

copyright:
  years: 2025
lastupdated: "2026-04-29"

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


Setup {{site.data.keyword.DR_full}} (PowerHA) helps you deploy and operate high-availability clusters by using PowerHA SystemMirror with minimal manual effort. The service integrates with IBM Cloud to streamline onboarding, cluster lifecycle operations, and service management for PowerHA-enabled virtual machines.

You can deploy PowerHA from the IBM Cloud catalog. The catalog guides you through selecting the PowerHA plan and associating existing PowerVS virtual machines that participate in a PowerHA cluster. The service focuses on automation, visibility, and lifecycle management, while cluster configuration and application setup remain customer-managed.
{: shortdesc}

## Why use PowerHA?
{: #why-use-powerha}

HA Automation for Power Virtual Server is a service that automates high availability for workloads that run on IBM Power Virtual Server, ensuring minimal downtime and fast failover.

“If a node in my cluster fails in an IBM Power Virtual Server environment, how does my application remain continuously available?”

Without automation, failover requires manual intervention to switch resources, mount storage, and restart applications, leading to service disruption.

PowerHA addresses by using a clustered environment with shared storage and heartbeat networks to monitor node health. When a failure is detected, PowerHA automatically moves the resource group to a standby node, imports volume groups, mounts file systems, and brings up the service IP and applications.

This ensures minimal downtime and continuous availability for applications that run on IBM Power Virtual Server.

## Before you begin
{: #prereqs}

Before you deploy HA Automation, ensure that the following requirements are met:

1. **Create an IBM Cloud account**: You must have an active IBM Cloud account. If required, sign up at [Sign up for IBM Cloud](https://cloud.ibm.com/registration).

2. **Configure IAM access** : Configure the required Identity and Access Management (IAM) roles and permissions for PowerHA. For more information, see [Managing PowerHA IAM access](/docs/dr-automation-powervs?topic=dr-automation-powervs-iam-manage).

3. **Genrate an API key** : An IBM Cloud API key is required for service provisioning and ongoing operations.


## Lifecycle of PowerHA
{: #lpvsdrauto}

Follow these steps to configure your PowerHA.

![PowerHA life Cycle](images/Power-ha-suits-flow-diagram.svg "PowerHA life Cycle"){: caption="PowerHA life Cycle" caption-side="bottom"}


## Next steps
{: #next-steps}

After configure your PowerHA, you can:

1. Validate the API key and select the High availability location and Power Virtual Server workspace.

2. Add the node and download the agent. For more information, see [Deploying the PowerHA SystemMirror](/docs/dr-automation-powervs?topic=dr-automation-powervs-deploying-ha-systemirror).
