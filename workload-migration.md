---

copyright:
  years: 2025
lastupdated: "2025-09-17"

subcollection: dr-automation

keywords: migration, migration deployment , upgrade, upgrade your deployment

---

# Planning a workload migration to {{site.data.keyword.DR_full}}
{: #plan-work-load}

When workloads are deployed on a new system, you must pay attention to its configuration and tuning to achieve the expected performance. {{site.data.keyword.DR_full_notm}} uses different IBM Power Systems: S922, E980, E1080, S1022.
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

## Upgrade your deployment
{: #Upgrade-dep-your}

This section provides a high-level walkthrough for migrating your existing deployment to the latest supported version. It outlines the essential steps for taking a snapshot from the source environment, restoring it on a new deployment, and completing the transition cleanly.

To migrate your current orchestrator to the latest version, complete the following steps:

1. Identify the Orchestrator VM from the workspace for your deployment.

2. Login in to the Orchestrator VM.

3. Check the current version of Orchestrator/KSYS using the following command:

   ```
   lslpp -l | grep ksys.license
   ```

   An output that is similar to the following example is displayed:

   ```
   ksys.license  1.8.0.1  COMMITTED  Base Server Runtime
   ```

   > **Note:** Migration is supported only if your deployment is running older versions of `ksys`. You can verify the supported `ksys` levels in the IBM VMRM DR for Power systems [Upgrading](https://www.ibm.com/docs/en/vmrmdr/1.8.0?topic=installing-upgrading) section .
   > If you're running an older version, proceed with the following steps to upgrade your Orchestrator (ksys) to the latest level.

4. To view the usage options for creating a snapshot, run the following command:

   ```
   ksysmgr add snapshot -h
   ```

   An output that is similar to the following example is displayed:

   ```
   ksysmgr add snapshot -h
         [filepath=<full file prefix path | file prefix>]
       add => ad*, cr*, make, mk
       snapshot => snap*
   ``` 

   - By default, the snapshot is created in the Orchestrator VM in the following path:
   ```
   `/var/ksys/snapshots`
   ```
   - You can create a snapshot with specified name prefix and directory using the following command :
   ```
   ksysmgr add snapshot filepath=/<directory>/<name>
   ```
   - The snapshot is created with a time stamp with the extension of `.tar.gz`
   ```
   snap.xml_DETAILED_2025-07-11_00:42:32.xml.tar.gz
   ```
  
5. Create a snapshot using the following command:

   ```bash
   ksysmgr add snapshot
   ```

   An output that is similar to the following example is displayed:
   
    ```
   Taking snapshot...
   Successfully created directory: /var/ksys/snapshots
   Successfully created directory for registry files: /var/ksys/snapshots/reg
   Created: /var/ksys/snapshots/snap.xml_DETAILED_2025-07-11_00:42:32.xml.tar.gz
   Successfully created a configuration snapshot: /var/ksys/snapshots/snap.xml_DETAILED_2025-07-11_00:42:32.xml.tar.gz
   ```
6. Now upload the snapshot manually to the IBM COS bucket.

### Restore snapshot on new deployment

1. Identify your deployment to restore the snapshot.

2. Login to the Orchestrator VM.

3. Restore the snapshot using the following command from the snapshot which was uploaded to COS:

   ```bash
   ksysmgr restore snap filepath=<snapshot-name> download_from_cos=yes region=<Region> bucketname=<Bucket-Name>
   ```

   An output that is similar to the following example is displayed:

   ```bash
   ksysmgr restore snap filepath=snap.xml_DETAILED_2025-07-14_10:51:02.xml.tar.gz download_from_cos=yes region=us-south bucketname=dra-cos-bucket-dev

   Successfully downloaded a configuration snapshot snap.xml_DETAILED_2025-07-14_10:51:02.xml.tar.gz from cos bucket dra-cos-bucket-dev
   WARNING: This action would remove the existing VMRM configuration
   Do you wish to proceed? [y|n]
   y
   This may take a few minutes to safely remove the ksyscluster
   11:19:02  Removed tmp files successfully
   Cleaning up old configuration...!
   Restoring configuration...
   Creating cluster...
   Updating registry...
   Successfully restored registry files!
   Starting VMR daemon...
   Successfully restored snapshot: /var/ksys/snap.xml_DETAILED_2025-07-14_10:51:02.xml!
   Please run discovery to apply changes.
   INFO: Restore completed successfully
   ```
   - If you want to restore a snapshot from your node instead of COS, run the following command:
   ```bash
   ksysmgr restore snap -h
   ksysmgr restore snapshot
      filepath=<full file prefix path>
      [download_from_cos=<yes | no>]
      [region=<cos_region>]
      [bucketname=<cos_bucket_name>]
      [apikey=<apikey>]
    restore => resto*
    snapshot => snap*
    ```
   > **Note**: Copy the snapshot to the `Example:/snap1` directory on the node, and then restore it using the file path from that location.

    An output that is similar to the following example is displayed:
    ```bash
   ksysmgr restore snapshot filepath=/snap1/snap.xml_DETAILED_2025-07-15_07:12:02.xml.tar.gz
   WARNING: This action would remove the existing VMRM configuration
   Do you wish to proceed? [y|n]
   y
   This may take a few minutes to safely remove the ksysclsuter
   01:32:49  Removed tmp files successfully
   This may take a few minutes to remove the ksyscluster
   Cleaning up old configuration...!
   Restoring configuration...
   Creating cluster...
   Updating registry...
   Successfully restored registry files!
   Starting VMR daemon...
   Successfully restored snapshot:/snap1/snap.xml_DETAILED_2025-07-15_07:12:02.xml!
   Please run discovery to apply changes.
   INFO: Restore completed successfully
    ```

   > **Note:** The above command uses the API key stored in the orchestrator to access the COS bucket for downloading the snapshot.

4. After a successful restore, Setup two displays all configurations from Setup one.  

5. Cleanup the source deployment cluster.

6. Run the following command to view RSCT (Reliable Scalable Cluster Technology) peer domain details:

   ```bash
   lsrpdomain
   ```

   An output that is similar to the following example is displayed:

   ```
   Name  OpState RSCTActiveVersion MixedVersions TSPort GSPort
   QA_rjakka15JulyNonHA_Cluster Online  3.3.2.0           No            12347  12348
   ```

7. Cleanup the source deployment using the following commands:

- To delete the cluster on the source node, run the following command:

   ```bash
   rmrpdomain -f <peer-domain-name>
   ```

- Run the following command to verify if the cluster is deleted or not:

   ```bash
   ksysmgr q clu
   ```

### Final step
{: #fi-na-l}

Deprovision the source deployment from the **Manage DR page** using Delete Service under **Action** from the GUI.

> **Note:** The VM is removed automatically after 24 hours.
>
> **Note:** When planning the migration, ensure that the source and destination configurations are identical. Both must be either a single KSYS deployment or a KSYS HA deployment. Migration is not supported if the snapshot is taken from a single KSYS deployment and restored on a KSYS HA deployment, or in the opposite deployment configuration.


## Upgrade your ksys filsets
{: #Upgrade-fil-set}

The orchestrator upgrade process involves updating the orchestrator file set to the latest supported release. This ensures system stability, enhanced security, and access to the newest features and fixes. The upgrade is performed through a simple CLI command, making it straightforward to keep your deployment current and reliable.

### Procedure
{: #procedure-upgrade}

To upgrade your current fileset to the latest version, complete the following steps:

#### Standard upgrade
{: #standard-upgrade}

Used for routine updates, it checks the system and upgrades only new or missing filesets while skipping those already installed.

To upgrade the filest to the latest version, run the following command:

```
ksysmgr upgrade filesets
```
An output that is similar to the following example is displayed:

```
ksysmgr upgrade filesets
Downloading fileset
[##############################] 100.00% (297178681/297178681 bytes)
File saved as /tmp/filesets//2529A_61ksys190.tar.gz
+-----------------------------------------------------------------------------+
                    Pre-installation Verification...
+-----------------------------------------------------------------------------+
Verifying selections...done
Verifying requisites...done
Results...

WARNINGS
--------
  Problems described in this section are not likely to be the source of any
  immediate or serious failures, but further actions may be necessary or
  desired.

  Already Installed
  -----------------
  The number of selected filesets that are either already installed
  or effectively installed through superseding filesets is 18.  See
  the summaries at the end of this installation for details.

  NOTE:  Base level filesets may be reinstalled using the "Force"
  option (-F flag), or they may be removed, using the deinstall or
  "Remove Software Products" facility (-u flag), and then reinstalled.

  << End of Warning Section >>

+-----------------------------------------------------------------------------+
                   BUILDDATE Verification ...
+-----------------------------------------------------------------------------+
Verifying build dates...done
FILESET STATISTICS
------------------
   18  Selected to be installed, of which:
       18  Already installed (directly or via superseding filesets)
  ----
    0  Total to be installed


Pre-installation Failure/Warning Summary
----------------------------------------
Name                      Level           Pre-installation Failure/Warning
-------------------------------------------------------------------------------
ksys.drutils.rte          1.9.0.0         Already installed
ksys.ha.license           1.9.0.0         Already installed
ksys.hautils.rte          1.9.0.0         Already installed
ksys.license              1.9.0.0         Already installed
ksys.main.cmds            1.9.0.0         Already installed
ksys.main.msg.DE_DE.cmds  1.9.0.0         Already installed
ksys.main.msg.ES_ES.cmds  1.9.0.0         Already installed
ksys.main.msg.FR_FR.cmds  1.9.0.0         Already installed
ksys.main.msg.IT_IT.cmds  1.9.0.0         Already installed
ksys.main.msg.JA_JP.cmds  1.9.0.0         Already installed
ksys.main.msg.PT_BR.cmds  1.9.0.0         Already installed
ksys.main.msg.ZH_CN.cmds  1.9.0.0         Already installed
ksys.main.msg.ZH_TW.cmds  1.9.0.0         Already installed
ksys.main.msg.en_US.cmds  1.9.0.0         Already installed
ksys.main.rte             1.9.0.0         Already installed
ksys.ui.agent             1.9.0.0         Already installed
ksys.ui.common            1.9.0.0         Already installed
ksys.ui.server            1.9.0.0         Already installed

Filesets upgradation completed successfully.
```

**NOTE**: If the orchestrator filesets are already up to date, the system verifies and skips reinstallation.

#### Forced Upgrade
{: #force-upgrade}

Used when a force installation is needed, it force installs all orchestrator filesets regardless of their current status.

To upgrade the filest to the latest version, run the following command:

```
ksysmgr upgrade -f filesets
```
An output that is similar to the following example is displayed:

```
# ksysmgr -f upgrade filesets
Downloading fileset
[##############################] 100.00% (297178681/297178681 bytes)
File saved as /tmp/filesets//2529A_61ksys190.tar.gz
+-----------------------------------------------------------------------------+
                    Pre-installation Verification...
+-----------------------------------------------------------------------------+
Verifying selections...done
Verifying requisites...done
Results...

SUCCESSES
---------
  Filesets listed in this section passed pre-installation verification
  and will be installed.

  Selected Filesets
  -----------------
  ksys.drutils.rte 1.9.0.0                    # Base Server Runtime
  ksys.ha.license 1.9.0.0                     # Base Server Runtime
  ksys.hautils.rte 1.9.0.0                    # Base Server Runtime
  ksys.license 1.9.0.0                        # Base Server Runtime
  ksys.main.cmds 1.9.0.0                      # Base Server Runtime
  ksys.main.msg.DE_DE.cmds 1.9.0.0            # Base Server Runtime - German
  ksys.main.msg.ES_ES.cmds 1.9.0.0            # Base Server Runtime - Spanish
  ksys.main.msg.FR_FR.cmds 1.9.0.0            # Base Server Runtime - French
  ksys.main.msg.IT_IT.cmds 1.9.0.0            # Base Server Runtime - Italian
  ksys.main.msg.JA_JP.cmds 1.9.0.0            # Base Server Runtime - Japanese
  ksys.main.msg.PT_BR.cmds 1.9.0.0            # Base Server Runtime - Brazil...
  ksys.main.msg.ZH_CN.cmds 1.9.0.0            # Base Server Runtime - Simpli...
  ksys.main.msg.ZH_TW.cmds 1.9.0.0            # Base Server Runtime - Tradit...
  ksys.main.msg.en_US.cmds 1.9.0.0            # Base Server Runtime - U.S. E...
  ksys.main.rte 1.9.0.0                       # Base Server Runtime
  ksys.ui.agent 1.9.0.0                       # VMRestart User Interface - a...
  ksys.ui.common 1.9.0.0                      # VMRestart User Interface - c...
  ksys.ui.server 1.9.0.0                      # VMRestart User Interface - s...

  << End of Success Section >>

+-----------------------------------------------------------------------------+
                   BUILDDATE Verification ...
+-----------------------------------------------------------------------------+
Verifying build dates...done
FILESET STATISTICS
------------------
   18  Selected to be installed, of which:
       18  Passed pre-installation verification
  ----
   18  Total to be installed

+-----------------------------------------------------------------------------+
                         Installing Software...
+-----------------------------------------------------------------------------+

installp: APPLYING software for:
        ksys.ui.server 1.9.0.0

Checking for the "vmruiserver" subsystem
Making sure the "vmruiserver" subsystem is not running...
The "vmruiserver" service is not running.
Removing the "vmruiserver" subsystem
0513-083 Subsystem has been Deleted.
    - Verify that vmruiinst.ksh been executed successfully.


. . . . . << Copyright notice for ksys.ui.server >> . . . . . . .
 Licensed Materials - Property of IBM

 5765VRM00
   Copyright International Business Machines Corp. 2016, 2025.

 All rights reserved.
 US Government Users Restricted Rights - Use, duplication or disclosure
 restricted by GSA ADP Schedule Contract with IBM Corp.
. . . . . << End of copyright notice for ksys.ui.server >>. . . .

Performing an SSH check...
Performing an OpenSSL check...
OpenSSL 3.0.10 1 Aug 2023 (Library: OpenSSL 3.0.10 1 Aug 2023)
Restoring files, please wait.
838 files restored.
1360 files restored.
2066 files restored.
2624 files restored.
3248 files restored.
4204 files restored.
4929 files restored.
5740 files restored.
7092 files restored.
8029 files restored.
8535 files restored.
9856 files restored.
11153 files restored.
11527 files restored.
12504 files restored.
13811 files restored.
14577 files restored.
15040 files restored.
16027 files restored.
17324 files restored.
18127 files restored.
18591 files restored.
19717 files restored.
20997 files restored.

Warning: One or more security files have already been established on this
         system (qa-migra11spt). They will not be overwritten.

Updating the GUI build
Creating the "vmruiserver" subsystem
0513-071 The vmruiserver Subsystem has been added.
Creating an inittab entry for vmruiserver
Starting the upgraded server
0513-059 The vmruiserver Subsystem has been started. Subsystem PID is 18481642.
Filesets processed:  1 of 18  (Total time:  18 mins 14 secs).

installp: APPLYING software for:
        ksys.ui.common 1.9.0.0


. . . . . << Copyright notice for ksys.ui.common >> . . . . . . .
 Licensed Materials - Property of IBM

 5765VRM00
   Copyright International Business Machines Corp. 2016, 2025.

 All rights reserved.
 US Government Users Restricted Rights - Use, duplication or disclosure
 restricted by GSA ADP Schedule Contract with IBM Corp.
. . . . . << End of copyright notice for ksys.ui.common >>. . . .

Restoring files, please wait.
1311 files restored.
2263 files restored.
3561 files restored.
4910 files restored.
Filesets processed:  2 of 18  (Total time:  21 mins 54 secs).

installp: APPLYING software for:
        ksys.ui.agent 1.9.0.0

Checking for the "vmruiagent" subsystem
Making sure the "vmruiagent" subsystem is not running...
The "vmruiagent" service is not running.
Removing the "vmruiagent" subsystem
0513-083 Subsystem has been Deleted.

. . . . . << Copyright notice for ksys.ui.agent >> . . . . . . .
 Licensed Materials - Property of IBM

 5765VRM00
   Copyright International Business Machines Corp. 2016, 2025.

 All rights reserved.
 US Government Users Restricted Rights - Use, duplication or disclosure
 restricted by GSA ADP Schedule Contract with IBM Corp.
. . . . . << End of copyright notice for ksys.ui.agent >>. . . .

Performing an SSH check...
Restoring files, please wait.
1314 files restored.
2329 files restored.
2774 files restored.
4088 files restored.
5410 files restored.
6176 files restored.
Creating the "vmruiagent" subsystem
0513-071 The vmruiagent Subsystem has been added.
Creating an inittab entry for vmruiagent
Filesets processed:  3 of 18  (Total time:  26 mins 43 secs).

installp: APPLYING software for:
        ksys.main.rte 1.9.0.0

IBM.VMR Daemon is active
IBM.VMR Deamon is active

. . . . . << Copyright notice for ksys.main.rte >> . . . . . . .
 Licensed Materials - Property of IBM

 5765VRM00
   Copyright International Business Machines Corp. 2016, 2025.

 All rights reserved.
 US Government Users Restricted Rights - Use, duplication or disclosure
 restricted by GSA ADP Schedule Contract with IBM Corp.
. . . . . << End of copyright notice for ksys.main.rte >>. . . .

IBM.VMR Daemon is active
Stopping KSYS...
Stopping RMC...
Starting RMC...
Filesets processed:  4 of 18  (Total time:  32 mins 54 secs).

installp: APPLYING software for:
        ksys.main.msg.en_US.cmds 1.9.0.0


. . . . . << Copyright notice for ksys.main.msg.en_US.cmds >> . . . . . . .
 Licensed Materials - Property of IBM

 5765VRM00
   Copyright International Business Machines Corp. 2016, 2025.

 All rights reserved.
 US Government Users Restricted Rights - Use, duplication or disclosure
 restricted by GSA ADP Schedule Contract with IBM Corp.
. . . . . << End of copyright notice for ksys.main.msg.en_US.cmds >>. . . .

Filesets processed:  5 of 18  (Total time:  32 mins 54 secs).

installp: APPLYING software for:
        ksys.main.msg.ZH_TW.cmds 1.9.0.0


. . . . . << Copyright notice for ksys.main.msg.ZH_TW.cmds >> . . . . . . .
 Licensed Materials - Property of IBM

 5765VRM00
   Copyright International Business Machines Corp. 2016, 2025.

 All rights reserved.
 US Government Users Restricted Rights - Use, duplication or disclosure
 restricted by GSA ADP Schedule Contract with IBM Corp.
. . . . . << End of copyright notice for ksys.main.msg.ZH_TW.cmds >>. . . .

Filesets processed:  6 of 18  (Total time:  32 mins 55 secs).

installp: APPLYING software for:
        ksys.main.msg.ZH_CN.cmds 1.9.0.0


. . . . . << Copyright notice for ksys.main.msg.ZH_CN.cmds >> . . . . . . .
 Licensed Materials - Property of IBM

 5765VRM00
   Copyright International Business Machines Corp. 2016, 2025.

 All rights reserved.
 US Government Users Restricted Rights - Use, duplication or disclosure
 restricted by GSA ADP Schedule Contract with IBM Corp.
. . . . . << End of copyright notice for ksys.main.msg.ZH_CN.cmds >>. . . .

Filesets processed:  7 of 18  (Total time:  32 mins 55 secs).

installp: APPLYING software for:
        ksys.main.msg.PT_BR.cmds 1.9.0.0


. . . . . << Copyright notice for ksys.main.msg.PT_BR.cmds >> . . . . . . .
 Licensed Materials - Property of IBM

 5765VRM00
   Copyright International Business Machines Corp. 2016, 2025.

 All rights reserved.
 US Government Users Restricted Rights - Use, duplication or disclosure
 restricted by GSA ADP Schedule Contract with IBM Corp.
. . . . . << End of copyright notice for ksys.main.msg.PT_BR.cmds >>. . . .

Filesets processed:  8 of 18  (Total time:  32 mins 56 secs).

installp: APPLYING software for:
        ksys.main.msg.JA_JP.cmds 1.9.0.0


. . . . . << Copyright notice for ksys.main.msg.JA_JP.cmds >> . . . . . . .
 Licensed Materials - Property of IBM

 5765VRM00
   Copyright International Business Machines Corp. 2016, 2025.

 All rights reserved.
 US Government Users Restricted Rights - Use, duplication or disclosure
 restricted by GSA ADP Schedule Contract with IBM Corp.
. . . . . << End of copyright notice for ksys.main.msg.JA_JP.cmds >>. . . .

Filesets processed:  9 of 18  (Total time:  32 mins 57 secs).

installp: APPLYING software for:
        ksys.main.msg.IT_IT.cmds 1.9.0.0


. . . . . << Copyright notice for ksys.main.msg.IT_IT.cmds >> . . . . . . .
 Licensed Materials - Property of IBM

 5765VRM00
   Copyright International Business Machines Corp. 2016, 2025.

 All rights reserved.
 US Government Users Restricted Rights - Use, duplication or disclosure
 restricted by GSA ADP Schedule Contract with IBM Corp.
. . . . . << End of copyright notice for ksys.main.msg.IT_IT.cmds >>. . . .

Filesets processed:  10 of 18  (Total time:  32 mins 57 secs).

installp: APPLYING software for:
        ksys.main.msg.FR_FR.cmds 1.9.0.0


. . . . . << Copyright notice for ksys.main.msg.FR_FR.cmds >> . . . . . . .
 Licensed Materials - Property of IBM

 5765VRM00
   Copyright International Business Machines Corp. 2016, 2025.

 All rights reserved.
 US Government Users Restricted Rights - Use, duplication or disclosure
 restricted by GSA ADP Schedule Contract with IBM Corp.
. . . . . << End of copyright notice for ksys.main.msg.FR_FR.cmds >>. . . .

Filesets processed:  11 of 18  (Total time:  32 mins 58 secs).

installp: APPLYING software for:
        ksys.main.msg.ES_ES.cmds 1.9.0.0


. . . . . << Copyright notice for ksys.main.msg.ES_ES.cmds >> . . . . . . .
 Licensed Materials - Property of IBM

 5765VRM00
   Copyright International Business Machines Corp. 2016, 2025.

 All rights reserved.
 US Government Users Restricted Rights - Use, duplication or disclosure
 restricted by GSA ADP Schedule Contract with IBM Corp.
. . . . . << End of copyright notice for ksys.main.msg.ES_ES.cmds >>. . . .

Filesets processed:  12 of 18  (Total time:  32 mins 58 secs).

installp: APPLYING software for:
        ksys.main.msg.DE_DE.cmds 1.9.0.0


. . . . . << Copyright notice for ksys.main.msg.DE_DE.cmds >> . . . . . . .
 Licensed Materials - Property of IBM

 5765VRM00
   Copyright International Business Machines Corp. 2016, 2025.

 All rights reserved.
 US Government Users Restricted Rights - Use, duplication or disclosure
 restricted by GSA ADP Schedule Contract with IBM Corp.
. . . . . << End of copyright notice for ksys.main.msg.DE_DE.cmds >>. . . .

Filesets processed:  13 of 18  (Total time:  32 mins 59 secs).

installp: APPLYING software for:
        ksys.main.cmds 1.9.0.0


. . . . . << Copyright notice for ksys.main.cmds >> . . . . . . .
 Licensed Materials - Property of IBM

 5765VRM00
   Copyright International Business Machines Corp. 2016, 2025.

 All rights reserved.
 US Government Users Restricted Rights - Use, duplication or disclosure
 restricted by GSA ADP Schedule Contract with IBM Corp.
. . . . . << End of copyright notice for ksys.main.cmds >>. . . .

Filesets processed:  14 of 18  (Total time:  33 mins 3 secs).

installp: APPLYING software for:
        ksys.hautils.rte 1.9.0.0


. . . . . << Copyright notice for ksys.hautils.rte >> . . . . . . .
 Licensed Materials - Property of IBM

 5765VRM00
   Copyright International Business Machines Corp. 2017, 2025.

 All rights reserved.
 US Government Users Restricted Rights - Use, duplication or disclosure
 restricted by GSA ADP Schedule Contract with IBM Corp.
. . . . . << End of copyright notice for ksys.hautils.rte >>. . . .

Filesets processed:  15 of 18  (Total time:  33 mins 7 secs).

installp: APPLYING software for:
        ksys.ha.license 1.9.0.0


. . . . . << Copyright notice for ksys.ha.license >> . . . . . . .
 Licensed Materials - Property of IBM

 5765VRM00
   Copyright International Business Machines Corp. 2018, 2025.

 All rights reserved.
 US Government Users Restricted Rights - Use, duplication or disclosure
 restricted by GSA ADP Schedule Contract with IBM Corp.
. . . . . << End of copyright notice for ksys.ha.license >>. . . .

Filesets processed:  16 of 18  (Total time:  33 mins 7 secs).

installp: APPLYING software for:
        ksys.drutils.rte 1.9.0.0


. . . . . << Copyright notice for ksys.drutils.rte >> . . . . . . .
 Licensed Materials - Property of IBM

 5765DRG00
   Copyright International Business Machines Corp. 2017, 2025.

 All rights reserved.
 US Government Users Restricted Rights - Use, duplication or disclosure
 restricted by GSA ADP Schedule Contract with IBM Corp.
. . . . . << End of copyright notice for ksys.drutils.rte >>. . . .

Filesets processed:  17 of 18  (Total time:  33 mins 11 secs).

installp: APPLYING software for:
        ksys.license 1.9.0.0


. . . . . << Copyright notice for ksys.license >> . . . . . . .
 Licensed Materials - Property of IBM

 5765DRG00
   Copyright International Business Machines Corp. 2016, 2025.

 All rights reserved.
 US Government Users Restricted Rights - Use, duplication or disclosure
 restricted by GSA ADP Schedule Contract with IBM Corp.
. . . . . << End of copyright notice for ksys.license >>. . . .

Finished processing all filesets.  (Total time:  33 mins 11 secs).

Please wait...

        /opt/rsct/install/bin/ctposti
0513-071 The ctrmc Subsystem has been added.
0513-059 The ctrmc Subsystem has been started. Subsystem PID is 18284962.
0513-059 The IBM.VMR Subsystem has been started. Subsystem PID is 19268008.
0513-059 The IBM.ConfigRM Subsystem has been started. Subsystem PID is 19464516.
done
+-----------------------------------------------------------------------------+
                                Summaries:
+-----------------------------------------------------------------------------+

Installation Summary
--------------------
Name                        Level           Part        Event       Result
-------------------------------------------------------------------------------
ksys.ui.server              1.9.0.0         USR         APPLY       SUCCESS
ksys.ui.server              1.9.0.0         ROOT        APPLY       SUCCESS
ksys.ui.common              1.9.0.0         USR         APPLY       SUCCESS
ksys.ui.agent               1.9.0.0         USR         APPLY       SUCCESS
ksys.ui.agent               1.9.0.0         ROOT        APPLY       SUCCESS
ksys.main.rte               1.9.0.0         USR         APPLY       SUCCESS
ksys.main.rte               1.9.0.0         ROOT        APPLY       SUCCESS
ksys.main.msg.en_US.cmds    1.9.0.0         USR         APPLY       SUCCESS
ksys.main.msg.ZH_TW.cmds    1.9.0.0         USR         APPLY       SUCCESS
ksys.main.msg.ZH_CN.cmds    1.9.0.0         USR         APPLY       SUCCESS
ksys.main.msg.PT_BR.cmds    1.9.0.0         USR         APPLY       SUCCESS
ksys.main.msg.JA_JP.cmds    1.9.0.0         USR         APPLY       SUCCESS
ksys.main.msg.IT_IT.cmds    1.9.0.0         USR         APPLY       SUCCESS
ksys.main.msg.FR_FR.cmds    1.9.0.0         USR         APPLY       SUCCESS
ksys.main.msg.ES_ES.cmds    1.9.0.0         USR         APPLY       SUCCESS
ksys.main.msg.DE_DE.cmds    1.9.0.0         USR         APPLY       SUCCESS
ksys.main.cmds              1.9.0.0         USR         APPLY       SUCCESS
ksys.main.cmds              1.9.0.0         ROOT        APPLY       SUCCESS
ksys.hautils.rte            1.9.0.0         USR         APPLY       SUCCESS
ksys.hautils.rte            1.9.0.0         ROOT        APPLY       SUCCESS
ksys.ha.license             1.9.0.0         USR         APPLY       SUCCESS
ksys.drutils.rte            1.9.0.0         USR         APPLY       SUCCESS
ksys.drutils.rte            1.9.0.0         ROOT        APPLY       SUCCESS
ksys.license                1.9.0.0         USR         APPLY       SUCCESS
Filesets upgradation completed successfully.
```
