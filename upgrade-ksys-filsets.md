---

copyright:
  years: 2025
lastupdated: "2025-10-09"

subcollection: dr-automation

keywords: upgrade your deployment, migration , migrate, ksys filsets, ksys

---

# Upgrade your ksys filsets
{: #Upgrade-fil-set}

The KSYS fileset upgrades the Orchestrator to the latest supported version to ensure compatibility with new features and improvements. Upgrading ksys to the latest version helps maintain system stability, enhance security, and provide access to the newest features and fixes. Before starting the upgrade, verify the currently installed version by running the following command:

```ksysmgr q version```

Ensure that the target version is the latest supported release is `Ksysmgr version: 1.9.0.0` and `Ksys version: 1.9.0.0` before proceeding. The upgrade process is performed through a simple CLI command, making it straightforward to keep your deployment current, reliable, and optimized.

### Procedure
{: #procedure-upgrade}

To upgrade your current ksys fileset to the latest version, complete the following steps:

#### Standard upgrade
{: #standard-upgrade}

For routine updates, the system checks and installs new or missing filesets while skipping those already present. If the orchestrator ksys filesets are up to date, the system verifies them and skips reinstallation.

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
To validate the upgrade is successful, run the following command to verify:

```
ksysmgr q version
```

Also you can Check [orchestrator and service details page](/docs/dr-automation-powervs?topic=dr-automation-powervs-or-ser-de) it displays the timestamp of your latest update and you can check in the event log to verify.

#### Forced Upgrade
{: #force-upgrade}

Use when a force installation is needed, it force installs all orchestrator ksys filesets regardless of their current status.

To upgrade the ksys filest to the latest version, run the following command:

```
ksysmgr upgrade -f filesets
```
An output that is similar to the following example is displayed:

```
# ksysmgr upgrade -f filesets
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
To validate the upgrade is successful, run the following command to verify:

```
ksysmgr q version
```
Also you can Check [orchestrator and service details page](/docs/dr-automation-powervs?topic=dr-automation-powervs-or-ser-de) it displays the timestamp of your latest update and you can check in the event log to verify.
