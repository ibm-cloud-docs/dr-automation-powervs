---

copyright:
  years: 2025
lastupdated: "2025-10-10"

subcollection: dr-automation

keywords: migration, migration deployment , upgrade, upgrade your deployment, snapshot

---

# Migratation planning in {{site.data.keyword.DR_full}}
{: #plan-work-load}



The orchestrator fileset upgrades the latest supported version to ensure compatibility with new features and improvements. Upgrading ksys to the latest version helps maintain system stability, enhance security, and provide access to the newest features and fixes. Before starting the upgrade, verify the currently installed version by running the following command:

```ksysmgr query version```

Ensure that the target version is the latest supported release, see [VMRM](https://www.ibm.com/docs/en/vmrmdr) page before proceeding. For the service pack version of the latest release check release notes of VMRM documentation for upgrade. The upgrade process is performed through a simple CLI command, making it straightforward to keep your deployment current, reliable, and optimized.

## Strategies
{: #mig-ra-tion}

This section provides a high-level walkthrough for upgrading your existing deployment to the latest supported version. It outlines the essential steps for taking a snapshot from the source environment, restoring it on a new deployment, and completing the transition cleanly.

Check the current Orchestrator version by running the following command:

```ksysmgr query version```

This display the current version number. Based on the version, choose one of two methods to migrate:

- [Migrate using snapshot backup and restore](#migrate-using-snapshot-backup-and-restore): If the current version is older than `1.9.0.1`. This involves taking a configuration snapshot on the source and restoring it onto a new deployment.
- [Migrate using direct approach](/docs/dr-automation-powervs?topic=dr-automation-powervs-Upgrade-fil-set): If the current version is `1.9.0.1` or later. This upgrades the existing deployment using the `ksysmgr upgrade file set` command.
