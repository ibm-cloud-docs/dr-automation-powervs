---

copyright:
  years: 2025
lastupdated: "2025-01-22"

subcollection: dr-automation

keywords: getting started

---

# Getting started with IBM {{site.data.keyword.DR_full_notm}}
{: #get-drauto}

{{site.data.keyword.DR_full}} is an disaster recovery offering. You can use {{site.data.keyword.DR_full_notm}} to automate disaster recovery (DR) processes for virtualized environments, ensuring continuity of operations with minimal manual intervention in the event of disasters or disruptions.
{:shortdesc: .shortdesc}

With {{site.data.keyword.DR_short}}, you can quickly deploy a disaster recovery solution from the IBM Cloud Catalog UI, which provides an intuitive interface to select and configure recovery services. The solution automates the recovery of virtual machines (VMs) and workloads, leveraging IBM Cloud infrastructure to offer a flexible, scalable, and efficient DR process. You can provision DR capabilities that synchronize data and manage replication between sites to secure critical workloads.

You get robust, automated management that continuously monitors DR operations, reduces manual processes, and minimizes downtime. The DR automation solution supports IBM Cloud's global regions, offering low-latency failover capabilities and high availability options to meet your specific DR needs across multiple IBM Cloud locations. By using DR automation , you can simplify the DR setup and operation, leveraging IBM Cloud’s infrastructure to enhance business resilience.

Get started with {{site.data.keyword.DR_short}} today to ensure reliable and efficient disaster recovery for your business workloads.




## Before you Begin
{: #bub} 

Before you create your first instance, review the following prerequisites:

1. Create an IBM Cloud account. To create an IBM Cloud account, see [Signing up for the IBM Cloud](https://cloud.ibm.com/registration).

2. Review the Identity and Access Management (IAM) information at [Managing DR Automation (IAM)](/docs/dr-automation-powervs?topic=dr-automation-powervs-iam-manage).

3. Create a public and private SSH key to securely connect to your Power Virtual Server. For instructions on creating a public and private SSH key, see Adding an SSH key.

4. Plan and specify your infrastructure requirements and review the estimated cost using the [DR Automation Estimate pricing tool](https://cloud.ibm.com/estimator).

5. Review the lifecycles of Power Virtual Server instances on IBM Power Virtual Server DR Automation.

## Lifecycle of Power Virtual Server DR Automation
{: #lpvsdrauto} 

![DR Automation life Cycle](images/dr-automation-blockdiagram.svg "DR Automation life Cycle"){: caption="DR Automation life Cycle" caption-side="bottom"}
