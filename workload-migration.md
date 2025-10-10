---

copyright:
  years: 2025
lastupdated: "2025-10-10"

subcollection: dr-automation

keywords: migration, migration deployment , upgrade, upgrade your deployment, snapshot

---

# Migrate using snapshot, backup and restore in {{site.data.keyword.DR_full}}
{: #plan-work-load}

When workloads are deployed on a new system, you must pay attention to its configuration and tuning to achieve the expected performance. {{site.data.keyword.DR_full_notm}} uses different IBM Power Systems: S922, E980, E1080, S1022, E1080, E1050 and S1122.
{:shortdesc: .shortdesc}

For more information on hardware specifications that you might need, see [Hardware specifications for {{site.data.keyword.DR_full_notm}}](/docs/dr-automation-powervs?topic=dr-automation-powervs-arch#hs).

For AIX, {{site.data.keyword.DR_full_notm}} supports only AIX 7.3, or later. If you use an unsupported version, it is subject to outages during planned maintenance windows with no advanced notification given.

## Migration Strategies
{: #mig-ra-tion}

This section provides a high-level walkthrough for upgrading your existing deployment to the latest supported version. It outlines the essential steps for taking a snapshot from the source environment, restoring it on a new deployment, and completing the transition cleanly.

Check the current Orchestrator version by running the following command:

```ksysmgr query version```

This display the current version number. Based on the version, choose one of two methods to migrate:

- [Migrate using snapshot backup and restore](#migrate-using-snapshot-backup-and-restore): If the current version is older than `1.9.0.1`. This involves taking a configuration snapshot on the source and restoring it onto a new deployment.
- [Migrate using direct approach](/docs-draft/dr-automation-powervs?topic=dr-automation-powervs-Upgrade-fil-set): If the current version is `1.9.0.1` or later. This upgrades the existing deployment using the `ksysmgr upgrade file set` command.
