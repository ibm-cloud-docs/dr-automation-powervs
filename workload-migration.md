---

copyright:
  years: 2025
lastupdated: "2025-10-09"

subcollection: dr-automation

keywords: migration, migration deployment , upgrade, upgrade your deployment, snapshot

---

# Backing up and restoring the configuration data of KSYS in {{site.data.keyword.DR_full}}
{: #plan-work-load}

When workloads are deployed on a new system, you must pay attention to its configuration and tuning to achieve the expected performance. {{site.data.keyword.DR_full_notm}} uses different IBM Power Systems: S922, E980, E1080, S1022 and Power11.
{:shortdesc: .shortdesc}

For more information on hardware specifications that you might need, see [Hardware specifications for {{site.data.keyword.DR_full_notm}}](/docs/dr-automation-powervs?topic=dr-automation-powervs-arch#hs).

For AIX, {{site.data.keyword.DR_full_notm}} supports only AIX 7.3, or later. If you use an unsupported version, it is subject to outages during planned maintenance windows with no advanced notification given. Your current AIX level and POWER processor family can help determine which migration path to follow.

## Migration checklist
{: #check-list}

Before you migrate to a newer IBM Power systems, review the following checklist:

1. Plan the system migration.
2. Install the latest required software and apply the available fixes.
3. Set the appropriate processor compatibility mode for logical partitions (LPARs) before and after migration.
4. Plan the virtual processor (VP) and entitlement for each LPAR to best fit your operation and performance requirements.
5. Consider contacting [IBM Technology Expert Labs](https://www.ibm.com/products/expertlabs) to ease the migration process.

## Lab services
{: #lab-service}

[IBM Technology Expert Labs](https://www.ibm.com/products/expertlabs) has service offerings available to assist you with resolving system, application, and database performance problems. Formal and informal training opportunities are also available where you can learn how to use performance tools and resolve issues on your own.
