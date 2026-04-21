---

copyright:
  years: 2025
lastupdated: "2026-04-21"

keywords: getting started, disaster recovery, PowerVS, start

subcollection: dr-automation-powervs

content-type: tutorial
services: 
account-plan: paid
completion-time: 10m

---

{{site.data.keyword.attribute-definition-list}}

# Getting started with DR Automation for Power Virtual Server
{: #getting-started}
{: toc-content-type="tutorial"}
{: toc-services=""}
{: toc-completion-time="10m"}

Set up {{site.data.keyword.DR_full}} **DR Automation** to automate disaster recovery processes for virtualized environments and ensure business continuity with minimal manual intervention. Deploy DR automation from the IBM Cloud catalog UI, which provides an intuitive interface for selecting and configuring recovery services. The solution automates the recovery of virtual machines (VMs) and workloads, synchronizing data, and managing replication between sites to protect critical operations.

IBM Power Virtual Server Public Cloud officially supports Red Hat Enterprise Linux (RHEL), IBM i, and IBM AIX® operating systems for creating virtual servers and configuring them as managed virtual machines to enable DR. With robust automation, DR Automation minimizes downtime, reduces manual tasks, and enhances business resilience. Using IBM Cloud's global regions, it offers low-latency failover and high availability options to effectively meet your DR requirements.
{: shortdesc}

## Why use DR Automation?
{: #why-use-dr-automation}

“If a site failure occurs in an IBM Power Virtual Server environment, how are my virtual machines and applications recovered without manual intervention?”

In traditional setups, disaster recovery involves multiple manual steps such as data replication, VM recovery, network reconfiguration, and application startup. This process is time-consuming and increases the risk of errors and extended downtime.

DR Automation addresses this by orchestrating end-to-end disaster recovery. It integrates with replication services to keep data synchronized and uses the orchestrator (KSYS) to automate failover. During a failure, workloads are brought up at the recovery site in a defined sequence, ensuring consistency and meeting recovery time (RTO) and recovery point (RPO) objectives.

This ensures automated and reliable recovery for workloads running on IBM Power Virtual Server.


## Before you begin
{: #prereqs}

Complete the following prerequisites:

1. **IBM Cloud account**: Ensure that you have an IBM Cloud account, [Sign up for IBM Cloud](https://cloud.ibm.com/registration) if needed.
2. **IAM setup**: Configure Identity and Access Management (IAM) roles. See [Managing DR Automation (IAM)](/docs/dr-automation-powervs?topic=dr-automation-powervs-iam-manage).
3. **SSH keys or Secret Manager**: Generate a public and private SSH key or choose a **Public SSH key** from the Secrets Manager. For details, see [Adding an SSH key](https://cloud.ibm.com/docs/account?topic=account-userapikey&interface=ui).

4. **Plan infrastructure**: Define your DR requirements and estimate costs by using the [DR Automation Estimate pricing tool](https://cloud.ibm.com/estimator).

## Lifecycle of Power Virtual Server DR Automation
{: #lpvsdrauto}

![DR Automation life Cycle](images/life-Cycle-public-private.svg "DR Automation life Cycle"){: caption="DR Automation life Cycle" caption-side="bottom"}

### Step 1: Set up the orchestrator
{: #setup-orchestrator}

1. On the **Manage tab**, enable or disable Orchestrator HA, configure the orchestrator name, and set a password to secure access.
2. Provide a valid **IBM Cloud API key**, then complete other fields, including the **DR location**, **DR Orchestrator networks** and **Public SSH key** or keys from **Secrets Manager**.

3. (Optional) Expand the **Advanced Orchestrator configuration** to enable MFA and provide proxy details. In the DR Orchestrator sections, select the required storage tier and machine type for the Orchestrator VMs. By default, Tier 1 storage and s922 machine type are selected.
4. If you have enabled **Orchestrator HA**, Provide standby orchestrator details.
5. Review all settings and click **Deploy Orchestrator** to begin the deployment.


## Next steps
{: #next-steps}

After completing the orchestrator setup, you can:

- [Manage virtual servers](/docs/dr-automation-powervs?topic=dr-automation-powervs-manage-vm-ser) that enables administrators to monitor and control the virtual server instances.

These advanced configurations help you optimize your disaster recovery setup for business resilience.
