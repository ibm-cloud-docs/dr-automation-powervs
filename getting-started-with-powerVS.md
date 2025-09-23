---

copyright:
  years: 2025
lastupdated: "2025-09-23"

keywords: getting started, disaster recovery, PowerVS

subcollection: dr-automation

content-type: tutorial
services: 
account-plan: paid
completion-time: 10m

---

{{site.data.keyword.attribute-definition-list}}

# Getting started with IBM {{site.data.keyword.DR_full_notm}}
{: #getting-started}
{: toc-content-type="tutorial"}
{: toc-services=""}
{: toc-completion-time="10m"}

Set up {{site.data.keyword.DR_full}} to automate disaster recovery (DR) processes for virtualized environments and ensure business continuity with minimal manual intervention. Deploy {{site.data.keyword.DR_short}} from the IBM Cloud Catalog UI, which provides an intuitive interface for selecting and configuring recovery services. The solution automates the recovery of virtual machines (VMs) and workloads, synchronizing data and managing replication between sites to protect critical operations.

IBM Power Virtual Server Public Cloud officially supports Red Hat Enterprise Linux (RHEL), IBM i, and IBM AIX® operating systems for creating virtual servers and configuring them as managed virtual machines to enable DR. With robust automation, {{site.data.keyword.DR_short}} minimizes downtime, reduces manual tasks, and enhances business resilience. Leveraging IBM Cloud's global regions, it offers low-latency failover and high availability options to effectively meet your DR requirements.
{: shortdesc}

## Before you begin
{: #prereqs}

Complete the following prerequisites:

1. **IBM Cloud account**: Ensure you have an IBM Cloud account, [Sign up for IBM Cloud](https://cloud.ibm.com/registration) if needed.
2. **IAM setup**: Configure Identity and Access Management (IAM) roles. See [Managing DR Automation (IAM)](/docs/dr-automation-powervs?topic=dr-automation-powervs-iam-manage).
3. **SSH keys or Secret Manager**: Generate a public and private SSH key or choose a **Public SSH key** from the Secrets Manager . For details, see [Adding an SSH key](https://cloud.ibm.com/docs/account?topic=account-userapikey&interface=ui).

4. **VPC Landing Zone schematic ID**: Ensure that a Power Virtual Server with a VPC Landing Zone schematic ID is available to enable connectivity to the orchestrator UI. You can either use an existing Power Virtual Server with a VPC Landing Zone schematic ID created through the catalog or create a new one. You can also import your existing VPC into Power Virtual Server with a VPC Landing Zone and generate a new schematic ID and use it. See [Power Virtual Server with VPC Landing Zone](https://cloud.ibm.com/docs/powervs-vpc?topic=powervs-vpc-automation-solution-overview) document.

5. **Plan infrastructure**: Define your DR requirements and estimate costs using the [DR Automation Estimate pricing tool](https://cloud.ibm.com/estimator).

## Lifecycle of Power Virtual Server DR Automation
{: #lpvsdrauto} 

![DR Automation life Cycle](images/Flow-chart-drawio.svg "DR Automation life Cycle"){: caption="DR Automation life Cycle" caption-side="bottom"}

### Step 1: Set up the orchestrator
{: #setup-orchestrator}

1. On the **Manage** tab, configure the **orchestrator name** and set a password to secure access.
2. Provide a valid **IBM Cloud API key**, then complete additional fields, including the **Schematics workspace** or **Custom VPC** and **Public SSH key** or keys from **Secrets Manager**.
   > **Note**: The schematic workspace is available if the VPC is created using the Power Virtual Server with VPC landing zone option from the catalog. If VPC is created manually, you can still generate a schematic ID using the Import option in the "Power Virtual Server with VPC landing zone" catalog or use the custom VPC option to provide the VPC details that are Transit Gateway, VPC name and Proxy IP details.
   
   > **Note**: Make sure provided API Key has permissions listed in the [Access role requirements for DR Automation for PowerVS](/docs/dr-automation-powervs?topic=dr-automation-powervs-iam-manage#ser-acc-role-dr-auto) for completing the configuration.

3. (Optional) Expand the **Advanced Configuration** to modify the default values of storage tier and machine type for the Orchestrator VM, by default **Tier1** is selected for Storage tier and **s922** is selected for machine type.

4. Provide standby orchestrator details, if you have enabled **Deploy Orchestrator with HA** on provision page.
5. Review all settings and click **Deploy Orchestrator** to begin the deployment.


## Next steps
{: #next-steps}

After completing the orchestrator setup, you can:

- [Manage virtual servers](/docs/dr-automation-powervs?topic=dr-automation-powervs-manage-vm-ser) that enables administrators to monitor and control the virtual server instances.



These advanced configurations help you optimize your disaster recovery setup for business resilience.
