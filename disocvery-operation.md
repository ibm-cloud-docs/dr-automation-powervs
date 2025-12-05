---
front_matter_title: "Discover"
lastupdated: "2024-10-23"
copyright: "2023, 2024"
subcollection: dr-automation-powervs
---
# Discovery operation
{: #dis-co-cover}

The discovery process in {{site.data.keyword.DR_full}}, accessible via the GUI, allows you to automatically identify and register essential resources across primary and backup sites. Users can initiate the discovery process, monitor its progress in real time, and verify that all critical virtual machines and network configurations are correctly identified and prepared for disaster recovery operations. This streamlined approach ensures readiness for failover with minimal manual intervention.

## Discover site
{: #diiiscover}

The Discover Site operation in {{site.data.keyword.DR_full_notm}} is essential for cataloging all resources at a site, including virtual machines and network configurations. This process ensures that the disaster recovery plan reflects the latest infrastructure changes. It should be performed during the initial setup of disaster recovery plans or after significant infrastructure updates to maintain accurate failover readiness.

### Steps to discover a site
{: #dissscover}

1. In the navigation pane of the {{site.data.keyword.DR_short}} GUI, select the site you want to discover.
2. Click **Discover Site**.
3. After the discovery process is successfully completed, the details are displayed in the [**Events tab**](/docs/dr-automation-powervs?topic=dr-automation-powervs-orch-events).

## Discover workGroup
{: #discoveer}


The Discover WorkGroup operation in {{site.data.keyword.DR_short}} is critical for cataloging all resources within a WorkGroup, including virtual machines, storage volumes, and network configurations. This ensures that the disaster recovery plan is updated to reflect the most recent infrastructure changes within the WorkGroup. This process should be carried out during disaster recovery setup or after any major updates to the WorkGroup to maintain accurate failover readiness.

### Steps to discover a WorkGroup
{: #discovvver}


1. In the navigation pane of the {{site.data.keyword.DR_short}} GUI, select the **WorkGroup** you want to discover.
2. Click **Discover WorkGroup**.
3. After the discovery process is successfully completed, the details are displayed in the [**Events tab**](/docs/dr-automation-powervs?topic=dr-automation-powervs-orch-events).
