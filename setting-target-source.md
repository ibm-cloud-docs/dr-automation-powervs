---

copyright:
  years: 2025
lastupdated: "2025-09-19"

subcollection: dr-automation

keywords: sites ksys, source site, target site, Source Satellite Location, Target Satellite Location, add node, configure sites

---

# Add sites to KSYS
{: #con-site-ksys}

Configure your environment by adding the **Source Site** and **Target Site**, specifying region names, and saving the configurations to enable seamless data replication.
{:shortdesc: .shortdesc}

Upon completing the KSYS setup, the DR Automation PowerVS GUI automatically redirects you to the **Add Sites** page.

**Note**: If you select **Client Location (Private pod)** as the cluster type while [Deploying the orchestrator](/docs/dr-automation-powervs?topic=dr-automation-powervs-idep-the-orch) , the Add sites page displays **Select Source Satellite Location** and **Select Target Satellite Location** instead of **Select Source Region** and **Select target Region**.

## Procedure
{: #aded-sitwe-ksyss}

To add sites, follow these steps:

1. On the **Add Sites** page.

2. Enter the details for the **Source Site** and **Target Site**, and select the appropriate regions from the list of available regions.

3. After completing the setup, click **Save & Next** and continue.

> **Note**: Add the node by clicking **Add Node** and provide the standby orchestrator IP. For More information see [Add Node](/docs/dr-automation-powervs?topic=dr-automation-powervs-nav-pan#ksys-set-tab-detai).

This setup ensures proper configuration of Source and Target sites, enabling efficient disaster recovery operations for your environment.
