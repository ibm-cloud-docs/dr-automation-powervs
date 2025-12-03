---
copyright:
  years: 2025
lastupdated: "2025-12-03"

subcollection: dr-automation-powervs

keywords: commands

---
# ksysmgr commands(Orchestrator)
{: #comm}

The command provides a consistent interface to configure the controller system (KSYS) and to perform {{site.data.keyword.DR_full}} operations by using a terminal or script.
{:shortdesc: .shortdesc}

## syntax
{: #syn}

    ksysmgr [-v] [-f] [-l {low|max}] [-i] 
    [-a {<ATTR#1>,<ATTR#2>,...}] <ACTION> <CLASS> [<NAME>]
    [-h | <ATTR#1>=<VALUE#1> <ATTR#2>=<VALUE#2> ...]

    ksysmgr [-v] [-f] [-l {low|max}] 
    [-a {<ATTR#1>,<ATTR#2>,...}] <ACTION> <CLASS> [<NAME>]
    <ATTR#1>=<VALUE#1> <ATTR#2>=<VALUE#2> ...]

         ACTION={add|modify|delete|query|manage|unmanage|...}\n\
         CLASS={ksyscluster|site|...}\n\

    ksysmgr {-h|-?} [-v] [<ACTION> [<CLASS>]]

    ksysmgr [-v] help

The basic format for using the ksysmgr command is as follows:

    ksysmgr ACTION CLASS [NAME] [ATTRIBUTES...]

>**Note:**
> - You must have root authority to run the ksysmgr command.
> - Help information is available for the ksysmgr command from the command line. For example, when you run the ksysmgr command without any flags or parameters a list of the available ACTIONs is displayed.
> - If you enter ksysmgr <ACTION> in the command line without specifying any CLASS, the command results in a list of all the available CLASSes for the specified ACTION.
> - Entering ksysmgr <ACTION> <CLASS> without specifying any NAME or ATTRIBUTES parameters is different because some ACTION and CLASS combinations do not require any additional parameters. To display help information in this scenario, you can view the help information by appending the -h flag to the ksysmgr <ACTION> <CLASS> command.
> - You cannot display help information from the command line for each of the ksysmgr command's ATTRIBUTES.

## Description
{: #des}

All ksysmgr command operations are logged in the ```/var/ksys/log/ksysmgr.oplog``` file, including the name of the executed command, start time, process ID for the ksysmgr operation, the command with arguments, and overall return code.

## ACTION
{: #act-ion}

The ```ACTION``` flags are not case-sensitive. All ```ACTION``` flags provide a shorter alias. For example, ```rm``` is an alias for ```delete```. Aliases are provided for convenience from the command line and must not be used in scripts.

The following ```ACTION``` flags are available:

>**Note**: The asterisk ```(*)``` in the aliases signify wildcard characters. For example, for the modify ACTION, the alias value is ```modd```. If you type ```mod*```, the command still works.

```query (alias: q*, ls, get, sh*)```

```add (alias: ad*, cr*, make, mk)```

```delete (alias: de*, remov*, rm, er*)```

```modify (alias: mod*, ch*, set)```

```restore (alias: rest*)```

```manage (alias: man*, mg)```

```unmanage (alias: unman*, umg)```

```discover (alias: di*)```

```move (alias: mov*, mv, swi*)```

```pair (alias: map)```

```refresh (ref*)```

```resync (resy*)```

```update (alias upd*)```

## CLASS
{: #cla-ss}

Specifies the type of object on which the ```ACTION``` is performed. The ```CLASS``` flags are not case-sensitive.

The following ```CLASS``` objects are supported:

```ksyscluster (alias: cl*, ksyscl*)```

 ```site (alias: sit*)```

```vm (alias: lp*, vm*)```

```notify (alias: rn, remote_not*, noti*)```

```snapshot (alias: snap*)```

```script (scr*)```

```workgroup (workg*, work_g*, wg)```

```disk```

```disk_group (dg, disk_g*)```

```event (ev*)```

```system (alias: sys*)```

```workspace (works*, work_s*, ws)```

```network (netw*, nw, net_work, net_w*)```

```region (regio*)```

## NAME
{: #nam}

Specifies the particular object, of type **CLASS** , on which the **ACTION** must be performed. The NAME flags are case-sensitive.

**ATTR=VALUE**

Specifies an optional flag that has attribute pairs and value pairs that are specific to the **ACTION** and **CLASS** combination. Use these pairs to specify configuration settings or to run particular operations. Both **ATTR** and **VALUE** flags are case-sensitive.

 ```-a {ATTR#1,ATTR#2,...}```

Displays only the specified attributes. This flag must be used with the query ACTION flag. For example:

```ksysmgr -a name, query site```

`-f`

Overrides any interactive prompts and forces the current operation to be run.

`-h`

Displays help information.

`-i`

Indicates that the ksysmgr command must prompt for your confirmation for important operations such as move operation across sites.

`-l low|max`

Activates the following trace logging values for troubleshooting purposes:

`low (default)`

Logs basic information for every ksysmgr operation.

`max`

Performs high tracing operations such as adding the routine function and the utility function. Adds transaction ID to the function's entry messages.

> Note: All trace data is written into the ksysmgr.log file. This flag is ideal for troubleshooting problems.

`-v`

Displays maximum verbosity in the output.

### Exit status
{: #exit}

**RC_UNKNOWN (Exit value = -1)**

Result is not known. This value is used as an initializer.

**RC_SUCCESS (Exit value = 0)**

No errors are detected. The operation is successful.

**RC_ERROR (Exit value = 1)**

An error occurred.

**RC_NOT_FOUND (Exit value = 2)**

The specified resource does not exist or cannot be found.

**RC_MISSING_INPUT (Exit value = 3)**

Required input is missing.

**RC_INCORRECT_INPUT (Exit value = 4)**

Detected input is incorrect.

## Examples
{: #example}

To get help information about the ksyscluster class, enter the following command:

```ksysmgr help ksyscluster```

An output that is similar to the following example is displayed:

```
Available actions for ksyscluster:
- add 
- delete 
- modify 
- query 
```

### To update license:
{: #update-lic}

```
ksysmgr update license -h

ksysmgr update license <vmname>
    update => upd*
    license => lic*
 Note: Only supports IBM i VM 
```

### Cluster configuration examples
{: #clu}

### To add a KSYS cluster:
{: #ksysclu}

```
ksysmgr add ksyscluster
      [<ksysclustername>]
      [type=<HA|DR|HADR|HADRHA|IBM_PVS_DR|IBM_PVS_PRIVATE_DR>]
      ksysnodes=<ksysnode1[,ksysnode2,...]>
      [sync=<yes|no>]
      apikey=<apikey>
      [baseurl=<baseurl>]
      [proxy=<ipaddress:portnumber>]
    add => ad*, cr*, make, mk
    ksyscluster => ksysclu*, clu*
    Note: apikey, baseurl and proxy are applicable only for IBM_PVS_DR cluster`
```

An output that is similar to the following example is displayed:

```
Adding node to current cluster configuration
Ksyscluster has been created, running verify now
Ksyscluster has been verified, running sync now
Stopping KSYS subsystem ...
Starting KSYS subsystem ...
KSYS subsystem has started. You can begin adding site definitions, etc
Note: By default, the value of type variable is DR cluster type.
```

### To update staticIP modification
{: #stats-modi}

```
ksysmgr modify vm -h

ksysmgr modify vm <vmname>
      [targetsystem=<target_system_type>]
      [staticIPMap=<srcip1-tgtip1,[srcip2-tgtip2,...]>]
    modify => mod*, ch*, set
    vm => lp*, vm*
```

### To query the KSYS cluster:
{: #quer}

```
ksysmgr query ksyscluster <ksysclustername>
query => q*, ls, get, sh*
ksyscluster => ksysclu*, clu*
```

An output that is similar to the following example is displayed:

```
# ksysmgr query cluster
Name: pvs_dr
State: Online
Type: IBM_PVS_DR
Ksysnodes: test.dev.com:1:Online
KsysState: test.dev.com:1:Online

```

An output that is similar to the following example is displayed for Private cloud:

```
# ksysmgr query cluster
Name:                test16sepprvi_Cluster
State:               Online
Type:                IBM_PVS_PRIVATE_DR
Ksysnodes:           testpriv1:1:Online
KsysState:           testpriv1:1:Online
Proxy:               10.30.40.4:3128
```

### To remove a KSYS cluster:
{: #removeksys}

```
ksysmgr [-f] delete ksyscluster <ksysclustername>
delete => de*, remove, rm, erase
ksyscluster => ksysclu*, clu*
```

When you delete a KSYS cluster, the **ksysmgr** command prompts for your confirmation. The **ksysmgr** command also recommends to create a snapshot at this point. 

An output that is similar to the following example is displayed:

```
WARNING: This action will remove all configuration and destroy the KSYS setup. It's recommended to create a backup with "ksysmgr add snapshot -h"
```

```
Do you want a backup to be created now ? [y|n]

`y`

Taking snapshot...
Created: /var/ksys/snapshots/oldclust_DETAILED_2024-07-29_06:35:30.xml.tar.gz
Successfully created a configuration snapshot: /var/ksys/snapshots/oldclust_DETAILED_2024-07-29_06:35:30.xml.tar.gz

Do you wish to store the logs on successful cluster deletion? [y|n]

`y`

Do you wish to proceed? [y|n]

`y`

This may take a few minutes to remove the `ksyscluster`


Automatic deep discovery disabled
Automatic quick discovery disabled
User_WG Workgroup stop VG has started
User_WG Workgroup stop VG has completed
Removal of VG disks from User_WG Workgroup has started
Removal of VG disks from User_WG Workgroup has completed
Workgroup User_WG was removed
vmrm_dev_01_WG Workgroup stop VG has started
vmrm_dev_01_WG Workgroup stop VG has completed
Removal of VG disks from vmrm_dev_01_WG Workgroup has started
Removal of VG disks from vmrm_dev_01_WG Workgroup has completed
Workgroup vmrm_dev_01_WG was removed
User_WG Workgroup stop VG has started
User_WG Workgroup stop VG has completed
Removal of VG disks from User_WG Workgroup has started
Removal of VG disks from User_WG Workgroup has completed
Workgroup User_WG was removed
Successfully created ksys logs backup /tmp/ksyscluster_logs_2024-07-29_06:36:05.tar.gz
IBM.VMR process stopped successfully
Peer domain was removed successfully
```

### To modify a KSYS cluster:
{: #modksys}

```
ksysmgr modify ksyscluster <ksysclustername> [glnode=<ksysnode>]
[add|remove]
[ksysnodes=<ksysnode1][,ksysnode2,...]>
[apikey=<apikey>]
[proxy=<ipaddress:portnumber>]
ksyscluster => ksysclu*, clu*
```

### To add a site in the KSYS subsystem:
{: #subsyste}

#### To add a site in the kSYS sub sytem for Public Cloud:
{: #subsyste-public-cloud}

```
ksysmgr add site <sitename> region=<regionname>
add => ad*
site => sit*
```

An output that is similar to the following example is displayed:

```
Waiting for update of Workspaces ...
Update of Workspaces are successful
Refresh VMs list of VMRM-Dal10 workspace started
Refresh VMs list of VMRM-Dal10 workspace completed
Refresh Networks list of VMRM-Dal10 workspace started
Refresh Networks list of VMRM-Dal10 workspace completed
Refresh VMs list of VMRM-TEST-DAL10 workspace started
Refresh VMs list of VMRM-TEST-DAL10 workspace completed
Refresh Networks list of VMRM-TEST-DAL10 workspace started
Refresh Networks list of VMRM-TEST-DAL10 workspace completed
Site dal10 added successfully
Note: dal10 partner GRS Region is us-east.
```

#### To add a site in the KSYS sub sytem Private cloud:
{: #subsyste-private-cloud}

```
ksysmgr add site -h
ksysmgr add site <sitename> satellitelocation=<satellitelocationname>
     add => ad*
     site => sit*
```

An output that is similar to the following example is displayed for Private cloud:

```
ksysmgr add site home satellitelocation=satloc_dal_clp2joc20ppo19876n50
Waiting for update of Workspaces ...
Update of Workspaces are successful
Refresh VMs list of Suv_Proc workspace started
Refresh VMs list of Suv_Proc workspace completed
Refresh Networks list of Suv_Proc workspace started
Refresh Networks list of Suv_Proc workspace completed
Refresh VMs list of SVT-SMALL-Q3.2-mano-GRS workspace started
Refresh VMs list of SVT-SMALL-Q3.2-mano-GRS workspace completed
Refresh Networks list of SVT-SMALL-Q3.2-mano-GRS workspace started
Refresh Networks list of SVT-SMALL-Q3.2-mano-GRS workspace completed
.
.
Refresh VMs list of test workspace started
Refresh VMs list of test workspace completed
Refresh Networks list of test workspace started
Refresh Networks list of test workspace completed
Site home added successfully
Note: satloc_dal_clp2joc20ppo19876n50 partner GRS Region(s) satloc_dal_cq8884h20ifkvm7quss0

```

### To query the details about a specific sites:
{: #details}

```
ksysmgr query site [<sitename>]
query => q*, ls, get, sh*
site => sit*
```

An output that is similar to the following example is displayed:

```
Name: us-east
Region: us-east
Workspaces: VMRM-wdc
ActiveWorkgroups: vmrm_dev_02_WG, vmrm_dev_03_WG, vmrm_dev_01_WG
Note: Active indicates the site where a WorkGroup's VMs are running. The same WorkGroup cannot be active on both sites, but others can be.
```

An output that is similar to the following example is displayed for Private cloud:
```
ksysmgr query site
Name:               backup
SatelliteLocation:  satloc_dal_cq8884h20ifkvm7quss0
Workspaces:         SVT-XSMALL-MANO-DND
                     WS-B
                     SVT_3Q2_XSPoD_25
                     SVT-XSMALL-Q3.2-mano-GRS
                     .......
                     test-xs-ws
Name:                home
SatelliteLocation:   satloc_dal_clp2joc20ppo19876n50
Workspaces:          Suv_Proc
                     SVT-SMALL-Q3.2-mano-GRS
                     ........
                     PerformanceTeam
                     test
```

### To delete a site:
{: #delets}

```
ksysmgr delete site <sitename>
delete => de*, remove, rm, erase
site => sit*
```

An output that is similar to the following example is displayed:

```
ksysmgr delete site us-east
Workspace VMRM-wdc was removed
Site us-east was removed
Workgroup configuration example
```
An output that is similar to the following example is displayed for Private cloud:
```
ksysmgr delete site home
Workspace Suv_Proc was removed
Workspace SVT-SMALL-Q3.2-mano-GRS was removed
......
Workspace PerformanceTeam was removed
Workspace test was removed
Site home was removed
Workgroup configuration example
```

### Manage virtual machine:
{: #manage-vm}

```
# ksysmgr manage disk -h
 
ksysmgr manage disk diskid=<diskid1[,diskid2,...]>
    manage => man*, mg
```
An output that is similar to the following example is displayed:



### To move a workgroup from one site to another site, run the following command:
{: #move-work}

```
ksysmgr move workgroup <name>
to=<site_name>
[force=<true|false>]
[dr_type=<planned|unplanned>]
move => mov*, mv, swi*
workgroup => workg*, work_g*, wg
```

### To query the details about a specific workgroup:
{: #quer}

```
ksysmgr query workgroup -h

ksysmgr query workgroup [ name ]
      [status [monitor=<no|yes>]]
    query => q*, ls, get, sh*
    workgroup => workg*, work_g*, wg
```

An output that is similar to the following example is displayed: 

```
ksysmgr query workgroup vmrm_IBMi_WG
Name:                vmrm_IBMi_WG
ID:                  2
VMs:                 vmrm_IBMi
PartnerVM:           vmrm_IBMi_BackUp
State:               READY_TO_MOVE
Priority:            Medium
SkipAutoResync:      OFF
HomeWorkSpace:       vmrm_powervsdr_dal12
BackupWorkSpace:     vmrm_powervsdr_wdc06
ActiveWorkspace:     vmrm_powervsdr_wdc06
Networks:            vmrm_dal12_network01 <-> vmrm_dal12_network01
CGName:              rccg-3b3d-b61c7

```
An output that is similar to the following example is displayed for private cloud:
```
ksysmgr query workgroup sb-aiz-01_WG
Name:                sb-aix-01_WG
ID:                  1
VMs:                 sb-aix-01
PartnerVM:           sb-aix-01_BackUp
State:               READY_TO_MOVE
Priority:            Medium
SkipAutoResync:      OFF
HomeWorkSpace:       SVT-SMALL-Q3.2-mano-GRS
BackupWorkSpace:     SVT_3Q2_XSPoD_25
ActiveWorkspace:     SVT-SMALL-Q3.2-mano-GRS
Networks:            net-30 <-> Testsubnet1
CGName:              rccg-3b3d-b61c7
```


### To discover all VMS in a specific workgroup for Dr readiness:
{: #dis-dr-read}

```
ksysmgr discover workgroup <name>
[monitor=<yes|no>]
discover => di*
workgroup => workg*, work_g*, wg
```
An output that is similar to the following example is displayed: 

```
ksysmgr -t discover workgroup User_test_WG
04:49:54 Running discovery on Workgroup User_test_WG, this may take a few minutes...
04:49:55 Discovery has started for Workgroup User_test_WG
04:49:55 Discovery has started for VM User_test
04:49:55 Discovery for VM User_test is complete
04:49:55 Replication enablement for volumes has started for VM User_test
04:51:01 Replication enablement for volumes has completed for VM User_test
04:51:01 Backup VM creation has started for VM User_test
04:51:01 Network Configuration has completed for VM User_test
04:51:47 Backup VM User_test_BackUp creation has completed
04:51:52 Discovery for Workgroup User_test_WG is complete
04:51:52 Replication is going on in background. Please use "ksysmgr query Workgroup status monitor=yes " to track the progress of the operation.
04:51:52 Discovery has finished for User_test_WG
1 out of 1 managed VMs have been successfully discovered
```

### To modify a workgroup:
{: #mow}

```
ksysmgr modify workgroup <name>
[priority=<Low|Medium|High>]
[SkipAutoResync=<ON|OFF>]
workgroup => workg*, work_g*, wg

```

### To resync a workgroup:
{: #resyn}

```
ksysmgr [-f] resync workgroup <workgroup_name>
resync => resy*
workgroup => workg*, work_g*, wg
```

An output that is similar to the following example is displayed: 

```
ksysmgr resync workgroup IBMi_WG
Workgroup IBMiWG resync has started
05:24:38 Shutdown has started for VM User_IBMi
05:24:54 Shutdown has completed for VM user_IBMi
05:24:57 Resync is in progress for Workgroup IBMiWG
05:26:08 Resync has completed for Workgroup IBMiWG
```

### LPAR configuration examples
{: #lpar}

To include or exclude a specific virtual machine from the KSYS configuration:

```
ksysmgr unmanage vm <vmname> | name=<vmname> | vmuuid=<uuid>
[workspace=<workspacename | ID>]
[force=<true|false>]
unmanage => unman*, umg
vm => lp*, VM
```

An output that is similar to the following example is displayed:

```
ksysmgr unmanage vm User_test
07:16:47 Unmanage vm has started, this may take a few minutes...
07:16:53 User_test_WG Workgroup stop VG has started
07:16:53 User_test_WG Workgroup stop VG has completed
07:16:53 Removal of VG disks from User_test_WG Workgroup has started
07:16:53 Removal of VG disks from User_test_WG Workgroup has completed
07:16:53 Workgroup User_test_WG was removed
VM User_test was successfully unmanaged
```

The preceding command syntax can be used for targeted VM management. The excluded virtual machine is not moved to the backup site when a site-switch operation is initiated.

> **Notes:** Including or excluding a virtual machine, you must run the discovery commands to rediscover the resources and validate the modified configuration setting.

### To update virtual machines:
{: #provirt}

```
ksysmgr modify vm -h

ksysmgr modify vm <vmname>
      [targetsystem=<target_system_type>]
      [staticIPMap=<srcip1-tgtip1,[srcip2-tgtip2,...]>]
    modify => mod*, ch*, set
    vm => lp*, vm*
```

## Discovery examples
{: #disvery}

### To discover the resources in a site:
{: #resdis}

```
ksysmgr discover site <sitename>
discover => di*
site => sit*
```

An output that is similar to the following example is displayed:
```
ksysmgr -t discover site us-east
02:33:39  Running discovery on entire site, this may take a few minutes...
        02:33:49  Discovery has started for Workgroup User_test_WG
        02:33:49  Discovery has started for Workgroup User_test_WG
        02:33:50  Discovery has started for VM User_test
       02:33:50  Discovery for VM User_test is complete
        02:33:50  Replication enablement for volumes has started for VM User_test
        02:33:50  Replication enablement for volumes has completed for VM User_test
        02:33:50  Backup VM creation has started for VM User_test
        02:33:50  Network Configuration has completed for VM User_test
        02:33:50  Discovery has started for VM User_test
        02:33:50  Discovery for VM User_test is complete
        02:33:50  Replication enablement for volumes has started for VM User_test
        02:33:50  Replication enablement for volumes has completed for VM User_test
        02:33:50  Backup VM creation has started for VM User_test
        02:33:50  Network Configuration has completed for VM User_test
        02:34:01  Backup VM User_test_BackUp creation has completed
        02:34:01  Backup VM User_test_BackUp creation has completed
        02:34:01  Discovery for Workgroup User_test_WG is complete
        02:34:01  Replication is going on in background. Please use "ksysmgr query Workgroup <wgname> status monitor=yes " to track the progress of the operation.
02:34:01  Discovery has finished for us-east
2 out of 2 managed VMs have been successfully discovered
```

### Script configuration examples
{: #scricon}

To add a script for automatic execution before or after the discovery and verification operations:
```
ksysmgr add script entity=<workgroup|site|vm>
[pre_offline=<full path to the script file>]
[post_offline=<full path to the script file>]
[pre_online=<full path to the script file>]
[post_online=<full path to the script file>]
[pre_discovery=<full path to the script file>]
[post_discovery=<full path to the script file>]
[pre_network_configuration=<full path to the script file>]
[post_network_configuration=<full path to the script file>]
[pre_storage_replication=<full path to the script file>]
[post_storage_replication=<full path to the script file>]
add => ad*, cr*, make, mk
script => scr*
Note: Network Configuration scripts are associated only with vm!
Note: Storage Replication scripts are associated only with workgroup!
Note: pre_online and post_offline scripts are not required at Site level!
```

## Events query examples
{: #abv}

### To query the event
{: #bvc}

```
ksysmgr query event [type=<error|warning|info>]
query => q*, ls, get, sh*
event => ev*
An output that is similar to the following example is displayed:
ksysmgr q event type=error
Current Notification Level: Low
Event Name Event Type Description
--------------------------------------------------------------------------------
| Location  | Replication Site | Is Active |
|-----------|-----------------|-----------|
| DISCOVERY_STARTED | info | true |
| DISCOVERY_FAILED | error | true |
| DISCOVERY_SUCCESS | info | true |
| MIGRATED_VM_EXISTS_IN_WG | error | true |
| DEPLOY_STARTED | info | true |
| DEPLOY_SUCCESS | info | true |
| DEPLOY_FAILED | error | true |
| GRS_ENABLE_VOLUMES_STARTED | info | true |
| GRS_ENABLE_VOLUMES_FAILED | error | true |
| GRS_ENABLE_VOLUMES_SUCCESS | info | true |
| ONBOARD_VOLUMES_STARTED | info | true |
| ONBOARD_VOLUMES_SUCCESS | info | true |
| ONBOARD_VOLUMES_FAILED | error | true |
| ATTACH_VOLUMES_STARTED | info | true |
| ATTACH_VOLUMES_SUCCESS | info | true |
| ATTACH_VOLUMES_FAILED | error | true |
| VM_SHUTDOWN_STARTED | info | true |
| VM_SHUTDOWN_SUCCESS | info | true |
| VM_SHUTDOWN_FAILED | error | true |
| VM_BOOTUP_STARTED | info | true |
| VM_BOOTUP_SUCCESS | info | true |
| VM_BOOTUP_FAILED | error | true |
| REPLICATION_MONITOR_STARTED | info | true |
| REPLICATION_MONITOR_SUCCESS | info | true |
| REPLICATION_MONITOR_FAILED | error | true |
| MOVE_STARTED | info | true |
| MOVE_SUCCESS | info | true |
| MOVE_FAILED | error | true |
| VG_REVERSAL_STARTED | info | true |
| VG_REVERSAL_SUCCESS | info | true |
| VG_REVERSAL_FAILED | error | true |
| VG_STOP_STARTED | info | true |
| VG_STOP_SUCCESS | info | true |
| VG_STOP_FAILED | error | true |
| VG_UPDATE_STARTED | info | true |
| VG_UPDATE_SUCCESS | info | true |
| VG_UPDATE_FAILED | error | true |
| VG_REMOVE_STARTED | info | true |
| VG_REMOVE_SUCCESS | info | true |
| VG_REMOVE_FAILED | error | true |
| VG_REMOVE_DISKS_STARTED | info | true |
| VG_REMOVE_DISKS_COMPLETED | info | true |
| VG_REMOVE_DISKS_FAILED | error | true |
| VM_REMOVE_STARTED | info | true |
| VM_REMOVE_SUCCESS | info | true |
| VM_REMOVE_FAILED | error | true |
| NETWORK_CONFIGURATION_STARTED | info | true |
| NETWORK_CONFIGURATION_SUCCESS | info | true |
| NETWORK_CONFIGURATION_FAILED | warning | true |
| VM_MISSED_FROM_WORKSPACE_PHASE | error | true |
| SCRIPT_FAILURE_EVENT | error | true |
| SCRIPT_SUCCESS_EVENT | info | true |
| NETWORK_CREATION_COMPLETED | info | true |


NETWORK_CONFIGURATION_FAILED warning Network configuration has failed.

```
 

#### To query the system-wide persistent attribute for the ksysmgr command, use the following command syntax:
{: #que-sys-wide}

```
ksysmgr query system [ properties ]
query => q*, ls, get, sh*
system => sys*
```

```
ksysmgr q system
```
An output that is similar to the following example is displayed:
```
System-Wide Persistent Attributes
BaseUrl: test.cloud.test.com
Regions: us-east
dal10
dal10
dal12
api_key: #####1543D972B94F CA61956C2392ED6B9AE5E6761 6197B2FBFFF42893275F2F9EBBCB5CF8C1A60E17EFCE765 9993178BC3B8E72FB68 CBC3D
trace_file_size: 1 MB
ksys_spooling: enable
spool_dest_dir: /tmp/ksys/rm
spool_dir_max_size: 1 MB
quick_discovery_interval: 60 minutes
quick_discovery: enable
deep_discovery: enable
cleanup_files_interval: 7 days
ksys_lang:
auto_discovery_time: 00:00 hours
custom_script_timeout: none
notification_level: low
dup_event_processing: yes
User Scripts for Site: None
User Scripts for Workgroup: None
User Scripts for VM: None
where,
auto_discovery_time
Sets time for daily discovery at each 24 hours a day.
min_redundancy_paths
Sets the minimum number of virtual Fiber Channel adapters that the VIOS requires for the virtual machine during a disaster recovery operation if the maximum number of virtual fibre channel adapters are not available.
lose_vios_redundancy
Sets the lose_vios_redundancy variable configuration.
notification_level
Notifies the generation of events based on severity of an event failure.
replication_type
Modifies the storage replication type.
vlanmap, vswitchmap
Sets the target site network on DR.
drvlanmap, drvswitchmap
Sets target site network on DR rehearsal
quick_discovery_interval
Sets the time duration for the quick discovery operation.
quick_discovery
Sets the quick_discovery variable to enable/disable.
deep_discovery
Sets the deep_discovery variable to enable/disable.
```


#### To modify the system wide persistent attribute for the ksysmgr command:
{: #mod-sys-wide}

```
ksysmgr modify system
[auto_discovery_time=<hh:mm>]
hh - hour: 00 to 23
mm - minute: 00 to 59
[quick_discovery_interval=<mm>]
mm - minute: 5 to 480
[quick_discovery=<enable | disable>]
[deep_discovery=<enable | disable>]
[trace_file_size=<MB>]
MB - Megabyte: Between 1 and 50 for single node KSYS cluster
Between 1 and 25 for Multiple node KSYS cluster
[ksys_spooling=<enable | disable>]
[spool_dest_dir=<path>]
[spool_dir_max_size=<MB>]
MB - Megabyte: Between 1 and 10240
[cleanup_files_interval=<disable | (1-30) days>]
[ksys_lang=<language>]
[notification_level=<low | medium | high | disable>]
[dup_event_processing=<yes | no>]
[custom_script_timeout=<sec>]
sec - seconds: Any positive integer
modify => mod*, ch*, set
system => sys*
Note: Not advisable to modify quick_discovery_interval with values less than 60 mins.
Note: If custom_script_timeout value is set to 0, it will be considered as no timeout is set.
Note: Supported locales for ksys_lang are DE_DE, FR_FR, JA_JP, PT_BR, ZH_TW, ES_ES, IT_IT, ZH_CN, en_US
By default language is considered to be en_US
```

### Quick discovery example
{: #qwe}

To enable or disable the quick-discovery feature:

```
ksysmgr modify system quick_discovery=enable
KSYS quick_discovery has been updated
```

To set the time duration for the quick-discovery operation:
```
KSYS quick_discovery_interval has been updated
```

## Notification configuration examples
{: #asf}

### To add an email for a specific user:
{: #ghj}

```
ksysmgr add notify
user=<username>
contact=<contact>
ksysmgr add notify
script=<full path script>
event=<event name>
add => ad*, cr*, make, mk
notify => rn, remote_not*, noti*
Note: Contact should be email address
```

An output that is similar to the following example is displayed:

```
ksysmgr add notify script=/User_test/a.sh event=DISCOVERY_STARTED successfully added script for event
```

### To modify an email address or script for a specific user:
{: #memail}

```
ksysmgr modify notify
oldcontact=<user name | user email>
newcontact=<user name | user email>
ksysmgr modify notify
oldscript=<custom_script>
newscript=<custom_script>
modify => mod*, ch*, set
notify => rn, remote_not*, noti*
```

An output that is similar to the following example is displayed:

```
ksysmgr modify notify oldcontact=User newcontact=sssssss
successfully modified user info
(0) root @ ksys804p: /
# ksysmgr q notify
Contact details:
User: sssssss
Contact: user.test.com
Script details:
Script: /User_test/a.sh
Event: DISCOVERY_FAILED
Script: /User_test/a.sh
Event: DISCOVERY_STARTED
```

### To query all the registered contact details:
{: #regis}

```
ksysmgr query notify [ contact | script ]
[ user=<username> | contact=<contact> ]
[ script=<full path script> ]
query => q*, ls, get, sh*
notify => rn, remote_not*, noti*
```

An output that is similar to the following example is displayed:
```
ksysmgr query notify
Contact details:
User: User
Contact: user.test.com
Script details: Script: /User_test/a.sh
Event: DISCOVERY_STARTED
```

### To delete all the contact information for a specific user:
{: #delet}

```
ksysmgr delete notify
user=<user name>
ksysmgr delete notify
script=<full path script> [ event=<event name> ]
delete => de*, remove, rm, erase
notify => rn, remote_not*, noti*
Note: User can give script name along with event name to remove notify for particular event.
Also, User can give Only script name to remove notify for all events listed with that script name
```

An output that is similar to the following example is displayed:
```
ksysmgr delete notify user="User"
successfully deleted user info
```

### To add a script for a predefined set of notifications and subsequent actions for a specific event:
{: #scrion}

```
ksysmgr add notify script=full_path_script event=event_name
```

For example,
```
ksysmgr add notify script=/User_test/a.sh event=DISCOVERY_STARTED successfully added script for event
```

### To modify a script:
{: #rfvn}

```
ksysmgr modify notify oldscript=old_file_name newscript=new_file_name
```

### To remove a script:
{: #ujm}

```
ksysmgr delete notify
user=<user name>
ksysmgr delete notify
script=<full path script> [ event=<event name> ]
delete => de*, remove, rm, erase
notify => rn, remote_not*, noti*
Note: User can give script name along with event name to remove notify for particular event.
Also, User can give Only script name to remove notify for all events listed with that script name

```

### To query a script:
{: query-scr}

```
ksysmgr query notify script
```

## System-wide attributes configuration
{: #dfg}


### To query details about system-wide attributes:
{: #opi}

```
ksysmgr query system -h

ksysmgr query system [ properties | status ]
    query => q*, ls, get, sh*
    system => sys*
```

An output that is similar to the following example is displayed:
```
ksysmgr query system
System-Wide Persistent Attributes
BaseUrl:                     cloud.test.com
Regions:                     wdc06
                             dal12
                             tok04
                             sao04
                             sao01
api_key:                     #####59E1857FA85240FDD689AC8AD81BC0F4CBBA447E7745DE85DFCD9DFEAB2D65D2B5 CB19CA18DEC1AC6E6A640BD2738ED9A 346C315CD9
staticipenable:              default
trace_file_size:             not set
ksys_spooling:               not set
spool_dest_dir:              not set
spool_dir_max_size:          not set
quick_discovery_interval:    60 minutes
quick_discovery:             enable
deep_discovery:              enable
cleanup_files_interval:      7 days
ksys_lang:
auto_discovery_time:         00:00 hours
custom_script_timeout:       none
notification_level:          low
dup_event_processing:        yes
User Scripts for Site: None
User Scripts for Workgroup: None
User Scripts for VM: None
```
An output that is similar to the following example is displayed for private cloud:
```
ksysmgr query system
System-Wide Persistent Attributes
BaseUrl:                     cloud.ibm.com
SatelliteLocations:          satloc_dal_clp2joc20ppo19876n50 - satloc_dal_cq8884h20ifkvm7quss0
api_key:                     #####16854C578FDCCF26592381C053 28F37FF3F7C 28E5039 9E1E6 398A87C8A 329A867 EEAA22CD5AC 435A65DBFA0819E3FC0F7E3A68BB4
staticipenable:              default
trace_file_size:             not set
ksys_spooling:               not set
spool_dest_dir:              not set
spool_dir_max_size:          not set
quick_discovery_interval:    60 minutes
quick_discovery:             enable
deep_discovery:              enable
cleanup_files_interval:      7 days
ksys_lang:
auto_discovery_time:         00:00 hours
custom_script_timeout:       none
notification_level:          low
dup_event_processing:        yes
User Scripts for Site: None
User Scripts for Workgroup: None
User Scripts for VM: None

```

Following is the output of modify system:

```
ksysmgr modify system -h

ksysmgr modify system
      [auto_discovery_time=<hh:mm>]
        hh - hour:   00 to 23
        mm - minute: 00 to 59
      [quick_discovery_interval=<mm>]
        mm - minute: 5 to 480
      [quick_discovery=<enable | disable>]
      [deep_discovery=<enable | disable>]
      [trace_file_size=<MB>]
        MB - Megabyte: Between 1 and 50 for single node KSYS cluster
                       Between 1 and 25 for Multiple node KSYS cluster
      [ksys_spooling=<enable | disable>]
      [spool_dest_dir=<path>]
      [spool_dir_max_size=<MB>]
        MB - Megabyte: Between 1 and 10240
      [cleanup_files_interval=<disable | (1-30) days>]
      [ksys_lang=<language>]
      [notification_level=<low | medium | high | disable>]
      [dup_event_processing=<yes | no>]
      [custom_script_timeout=<sec>]
        sec - seconds: Any positive integer
      [staticipenable=<yes|no|default>]
    modify => mod*, ch*, set
    system => sys*
Note: Not advisable to modify `quick_discovery_interval` with values less than `60 mins`.
Note: If `custom_script_timeout` value is set to `0`, it will be considered as no timeout is set.
Note: Supported locales for `ksys_lang` are `DE_DE, FR_FR, JA_JP, PT_BR, ZH_TW, ES_ES, IT_IT, ZH_CN, en_US`, by default language is considered to be `en_US`
```

### To enable the KSYS subsystem to rediscover the resources every day automatically:
{: #asd}

```
ksysmgr modify system deep_discovery=enable
KSYS deep_discovery has been updated
```

```
ksysmgr modify system quick_discovery=enable
KSYS quick_discovery has been updated
```

An output that is similar to the following example is displayed:

```
ksysmgr modify system auto_discovery_time=07:31:28
KSYS auto_discovery_time has been updated
ksysmgr modify system quick_discovery_interval=32
KSYS quick_discovery_interval has been updated
ksysmgr mod system quick_discovery=enable
KSYS quick_discovery has been updated
ksysmgr mod system quick_discovery=disable
KSYS quick_discovery has been updated
ksysmgr mod system deep_discovery=enable
KSYS deep_discovery has been updated
ksysmgr mod system deep_discovery=disable
KSYS deep_discovery has been updated
ksysmgr mod system trace_file_size=1
KSYS trace_file_size has been updated
Note: Spooling destination directory has been set to default path "/tmp/ksys/rm"
ksysmgr mod system ksys_spooling=enable
KSYS ksys_spooling has been updated
ksysmgr mod system ksys_spooling=disable
KSYS ksys_spooling has been updated
ksysmgr mod system cleanup_files_interval=1
KSYS cleanup_files_interval has been updated
ksysmgr mod system spool_dest_dir="/tmp/ksys/rm"
INFO: Attribute spool_dest_dir is already set to the specified value
ksysmgr mod system spool_dir_max_size=1
KSYS spool_dir_max_size has been updated
ksysmgr mod system ksys_lang=DE_DE
KSYS ksys_lang has been updated
ksysmgr mod system notification_level=low
KSYS notification_level has been updated
ksysmgr mod system dup_event_processing=yes
KSYS dup_event_processing has been updated
ksysmgr mod system custom_script_timeout=2
KSYS custom_script_timeout has been updated
Note: The value in the sa_ping_timer attribute and the hmc_ping_timer attribute must be in the range 10 and 30. You can view the configured value in the output of the ksysmgr query system command.
```

### To change the notification level of your system to receive notification for all critical errors and warnings of all events:
{: #zsx}

```
ksysmgr modify system notification_level=high
```

### To change the duplicate event processing option to receive notification for all events, even if the events are duplicated:
{: #xdr}

```
ksysmgr modify system dup_event_processing=no
```

## Disaster recovery operation examples
{: #tgf}

### To initiate a site-switch operation:
{: #isw}

```
ksysmgr [-f] move site
from=<sitename>
to=<sitename>
[force=<true|false>]
[dr_type=<planned|unplanned>]
move => mov*, mv, swi*
site => sit*
Note: dr_type=planned is the default
```

If you do not specify the cleanup attribute, for a planned disaster recovery operation, the KSYS subsystem automatically cleans up the source site from where the site-switch operation was initiated.

## Snapshot examples
{: #snpe}

### To save a snapshot of the KSYS cluster configuration and resources:
{: #save}


```
ksysmgr add snapshot
[filepath=<full file prefix path | file prefix>]
add => ad*, cr*, make, mk
snapshot => snap*
```

An output that is similar to the following example is displayed:

```
ksysmgr add snapshot
Taking snapshot...
Created: /var/ksys/snapshots/snap.xml_DETAILED_2024-07-30_05:37:50.xml.tar.gz
Successfully created a configuration snapshot: /var/ksys/snapshots/snap.xml_DETAILED_2024-07-30_05:37:50.xml.tar.gz
```

### To view a snapshot, use the following command syntax:
{: #visnuse}


```
ksysmgr query snapshot
[filepath=<full file prefix path>]
query => q*, ls, get, sh*
snapshot => snap*
```

An output that is similar to the following example is displayed:
```
---- Snapshot Contents ----
File: /var/ksys/snapshots/oldclust_DETAILED_2024-07-29_06:35:30.xml
VMRM Version:1.8.0.1
Date: 2024-07-29
Time: 06:35:30
--------------------------
Cluster:
--------
Name: pvs_dr
Node: hostname.com
Type: IBM_PVS_DR
```

### To restore the configuration data on a KSYS node:
{: #data}

```
ksysmgr restore snapshot
filepath=<full file prefix path>
restore => resto*
snapshot => snap*
```

An output that is similar to the following example is displayed:

```
ksysmgr restore snapshot filepath=/var/ksys/snapshots/snap.xml_DETAILED_2024-07-28_01:15:14.xml.tar.gz
WARNING: This action would remove the existing VMRM configuration
Do you wish to proceed? [y|n]
y
This may take a few minutes to safely remove the ksysclsuter
01:15:44 Removed tmp files successfully
This may take a few minutes to remove the ksyscluster
01:15:54 User_test_WG Workgroup stop VG has started
01:15:54 User_test_WG Workgroup stop VG has completed
01:15:54 Removal of VG disks from User_test_WG Workgroup has started
01:15:54 Removal of VG disks from User_test_WG Workgroup has completed
01:15:54 Workgroup User_test_WG was removed
Restoring configuration...
Creating cluster...
Updating registry...
Successfully restored registry files!
Starting VMR daemon...
Successfully restored snapshot:/var/ksys/snapshots/snap.xml_DETAILED_2024-07-28_01:15:14.xml!
Please run discovery to apply changes.
INFO: Restore completed successfully
 ```


This command decompresses and unarchives the snapshot file, and then applies the configuration settings to the KSYS node.

## Disk group example
{: #groupstat}

### To query disk group, run the following command:
{: #speci}

```
ksysmgr query disk_group [wg=<wgname>]
    query => q*, ls, get, sh*
    disk_group => dg, disk_g*
```
An output that is similar to the following example is displayed:

```
ksysmgr query disk_group
WGName:              vmrm_rhel_WG
CGName:              rccg-a382-d35ba
CGState:             consistent_copying
Progress:            99.0
HomeWorkSpace:       vmrm_powervsdr_dal12
BackupWorkSpace:     vmrm_powervsdr_wdc06
ActiveWorkspace:     vmrm_powervsdr_dal12
Active Site:         DAL
VolumeDiskGroup:     vmrm_rhel_WG_VG <-> rccg-a382-d35ba

```
An output that is similar to the following example is displayed for private cloud:
```
ksysmgr q disk_group
WGName:              vmrm_rhel_WG
CGName:              rccg-a382-d35ba
CGState:             consistent_copying
Progress:            99.0
HomeWorkSpace:       SVT-SMALL-Q3.2-mano-GRS
BackupWorkSpace:     SVT_3Q2_XSPoD_25
ActiveWorkspace:     SVT-SMALL-Q3.2-mano-GRS
Active Site:         DAL
VolumeDiskGroup:     vmrm_rhel_WG_VG <-> rccg-a382-d35ba
```


## Viewing disk details
{: #diskdetail}

### To view the details of a disk, run the following command:
{: #runfollow}

```
ksysmgr query disk
vm=<vmname>
query => q*, ls, get, sh*
```

An output that is similar to the following example is displayed:

```
ksysmgr query disk vm=vmrm_rhel
VM:                  vmrm_rhel <-> vmrm_rhel_BackUp
CGName:              rccg-a382-d35ba
CGState:             consistent_copying
Progress:            99.0
DiskIDs:             volume-vmrm_rhel-8852d59e-000269ee-boot-0-34b22e2b-0aaf -> 34b22e2b-0aaf-4124-ad8e-4f76cdfb4cf8
Volume Details:
| Volume                                                                      | State                 | Progress (%) |
|----------------------------------------------------------------------------|-----------------------|--------------|
| volume-vmrm_rhel-8852d59e-000269... <-> aux_mrm_rhel-8852d59e-000269ee-b... | consistent_copying    | 99           |

```

### To manage disk on virtual machine:
{: #manage-disk-vm}

```
ksysmgr manage disk -h
 
ksysmgr manage disk diskid=<diskid1[,diskid2,...]>
    manage => man*, mg
```

### To unmanage disk on virtual machine:
{: #unmanage-disk-vm}

```
# ksysmgr unmanage disk -h
 
ksysmgr unmanage disk diskid=<diskid1[,diskid2,...]> workgroup=<workgroup_name>
    unmanage => unman*, umg
```

### To query a virtual machine disk:
{: #query-vm-disk}

```
 ksysmgr query disk vm=vmrm_aix_vm2
VM:                  vmrm_aix_vm2 <-> vmrm_aix_vm2_BackUp
CGName:              rccg-aca6-1507e
CGState:             consistent_copying
Progress:            99.66666666666667
DiskIDs:             volume-aix_vol2-2d5ff23a-13bb -> 2d5ff23a-13bb-43d8-b354-51603dee5e50
                     volume-aix_vol3-6a958988-9745 -> 6a958988-9745-4fee-8942-f8b80118e8e7
                     volume-vmrm_aix_vm2-bc477fa9-00046b90-boot-0-a69d29f9-bc3a -> a69d29f9-bc3a-424e-a91e-3edad82348a4

Volume Details:

| Volume | State | Progress (%) |
|---------|--------|--------------|
| `volume-aix_vol2-2d5ff23a-13bb <-> aux_volume-aix_vol2-2d5ff23a-13b...` | consistent_copying | 100 |
| `volume-aix_vol3-6a958988-9745 <-> aux_volume-aix_vol3-6a958988-974...` | consistent_copying | 100 |
| `volume-vmrm_aix_vm2-bc477fa9-000... <-> aux__aix_vm2-bc477fa9-00046b90-b...` | consistent_copying | 100 |
```

### To unmanage a disk on virtual machine:
{: #un-manage-vm-disk}

```
ksysmgr unmanage disk diskid=2d5ff23a-13bb-43d8-b354-51603dee5e50 workgroup=vmrm_aix_vm2_WG
DiskID(s) was successfully unmanaged
```

### To query unmanaged disk:
{: #un-manage-qu-disk}

```
ksysmgr query disk vm=vmrm_aix_vm2
VM:                  vmrm_aix_vm2 <-> vmrm_aix_vm2_BackUp
CGName:              rccg-aca6-1507e
CGState:             consistent_copying
Progress:            99.5
DiskIDs:             volume-aix_vol3-6a958988-9745 -> 6a958988-9745-4fee-8942-f8b80118e8e7
                     volume-vmrm_aix_vm2-bc477fa9-00046b90-boot-0-a69d29f9-bc3a -> a69d29f9-bc3a-424e-a91e-3edad82348a4
                     2d5ff23a-13bb-43d8-b354-51603dee5e50 -> Unmanaged
Volume Details

| Volume | State | Progress (%) |
|---------|--------|--------------|
| `volume-aix_vol3-6a958988-9745 <-> aux_volume-aix_vol3-6a958988-974...` | consistent_copying | 100 |
| `volume-vmrm_aix_vm2-bc477fa9-000... <-> aux__aix_vm2-bc477fa9-00046b90-b...` | consistent_copying | 100 |
```

## KSYS spooling
{: #spooling}


### To query a KSYS spooling:
{: #query}


```
ksysmgr query system [ properties ]
query => q*, ls, get, sh*
system => sys*
```

An output that is similar to the following example is displayed:

```
ksysmgr modify system trace_file_size=30 ksys_spooling=enable spool_dest_dir=/tmp
KSYS spool_dest_dir,ksys_spooling,trace_file_size has been updated

trace_file_size:             30 MB
ksys_spooling:               enable
spool_dest_dir:              /tmp
```

### To enable KSYS spooling:
{: #to}

```
ksysmgr modify system ksys_spooling=enable
```

 >**Note:** If you enable the ksys_spooling and the spool_dest_dir value is not set for the KSYS spooling, then the spool_dest_dir will get a default value as /tmp/ksys/rm.


### To modify the KSYS spool_dir_max_size:
{: #dirmix}

```
ksysmgr modify system spool_dir_max_size=<value>
```

**Example:**
```
ksysmgr modify system spool_dir_max_size=10240
```

An output that is similar to the following example is displayed:
```
trace_file_size: 25 MB ksys_spooling: enable spool_dest_dir: /S1 spool_dir_max_size: 10240 MB hmc_ping_timer: 0 seconds
```

>**Note**: You will get an error message if the spool_dir_max_size value is greater than 10240 MB (10 GB).

### To modify the ksys_spooling, trace_file_size, and spool_dest_dir:
{: #trace}

```
ksysmgr modify system trace_file_size=<value> ksys_spooling=<enable/disable> spool_dest_dir=<path>
```

An output that is similar to the following example is displayed:

```
ksysmgr modify system trace_file_size=30 ksys_spooling=enable spool_dest_dir=/tmp
KSYS spool_dest_dir,ksys_spooling,trace_file_size has been updated

trace_file_size:             30 MB
ksys_spooling:               enable
spool_dest_dir:              /tmp
```

## Notification configuration and query example
{: #quexconf}

### To add a notification, run the following command:
{: #vqwe}

```
ksysmgr add notify 
 user=<username>
 contact=<contact>
ksysmgr add notify 
      script=<full path script> 
      event=<event name>
add => ad*, cr*, make, mk
notify => rn, remote_not*, noti*
```

An output that is similar to the following example is displayed:

```
ksysmgr add notify script=/User_test/a.sh event=DISCOVERY_STARTED 
Successfully added script for event
```

### To query notification details, run the following command:
{: #commae}

```
ksysmgr query notify [ contact | script ]
[ user=<username> | contact=<contact> ]
[ script=<full path script> ]
query => q*, ls, get, sh*
notify => rn, remote_not*, noti*
```
An output that is similar to the following example is displayed:
```
ksysmgr query notify
Contact details:
User: User 
Contact: user.test.com
Script details:
Script: /User_test/a.sh 
Event: DISCOVERY_STARTED
```

### To delete a notification, run the following command:
{: #todelete}

```
ksysmgr delete notify
      user=<username>
```
An output that is similar to the following example is displayed:

```
ksysmgr delete notify user="User" 
Successfully deleted user info.
```

## Snapshot configuration example
{: #snapshot}

### To add a snapshot, run the following command:
{: #visnuserun}

```
ksysmgr add snapshot 
[filepath=<full file prefix path | file prefix>]
add => ad*, cr*, make, mk
snapshot => snap*
```

An output that is similar to the following example is displayed:

```
ksysmgr add snapshot 
Taking snapshot...
Created: /var/ksys/snapshots/snap.xml_DETAILED_2024-07-30_05:37:50.xml.tar.gz 
Successfully created a configuration snapshot: /var/ksys/snapshots/snap.xml_DETAILED_2024-07-30_05:37:50.xml.tar.gz
```

## Workspace pairing and refreshing example
{: #referesh}

### To pair a workspace, run the following command:
{: #pairs}

```
ksysmgr pair workspace -h
ksysmgr pair workspace <home_workspacename | ID>
      pair=<target_workspacename | ID> | pair=none
    pair => map
    workspace => works*, work_s*, ws
    Note: pair=none for unpairing the workspace
```
An output that is similar to the following example is displayed:

```
ksysmgr pair ws VMRM-Dal10 pair=VMRM-wdc
Workspace VMRM-Dal10 was paired with VMRM-wdc
```
An output that is similar to the following example is displayed for private cloud:
```
ksysmgr pair ws SVT-SMALL-Q3.2-mano-GRS pair=SVT_3Q2_XSPoD_25
Workspace SVT-SMALL-Q3.2-mano-GRS was paired with SVT_3Q2_XSPoD_25
```

## To refresh a workspace, run the following command:
{: #refereshert}

```
ksysmgr refresh workspace <workspacename>
refresh => ref*
workspace => works*, work_s*, ws
```

An output that is similar to the following example is displayed:

```
ksysmgr refresh workspace VMRM-wdc
Refresh workspaces to update Networks and VMs list completed.
```
An output that is similar to the following example is displayed for private cloud:
```
ksysmgr refresh workspace SVT_3Q2_XSPoD_25
Refresh workspaces to update Networks and VMs list completed.
```

## Network pairing example
{: #netpair}

### To pair a network, run the following command:
{: #runfollow}

```
ksysmgr pair network <source_network_name>
      pair=<target_network_name> | pair=none
      [home_workspace=<home_workspacename>]
      [target_workspace=<target_workspacename>]
      [ip_range=<start_ip_address,end_ip_address>]
      [cidr=<cidr>]
      [dns=<dns>]
    pair => map
    network => net*, net_w, nw
Note: pair=none for unpairing the network
```

An output that is similar to the following example is displayed:

```
ksysmgr pair network VMRM-Dal10-Network01 pair=vmrm-wdc-network01
Network VMRM-Dal10-Network01 was paired with vmrm-wdc-network01
```
An output that is similar to the following example is displayed for private cloud:

```
ksysmgr pair network net-30 pair=Testsubnet1
Network net-30 was paired with Testsubnet1
```

## Site discovery example
{: #disco}

### To discover a site, run the following command:
{: #sitedis}

```
ksysmgr discover site <sitename>
discover => di*
site => sit*
```

An output that is similar to the following example is displayed:

```
ksysmgr discover site DAL
05:31:41  Running discovery on entire site, this may take a few minutes...
        05:31:59  Discovery has started for Workgroup vmrm_rhel_WG
        05:31:59  Discovery has started for VM vmrm_rhel
        05:32:09  Discovery for VM vmrm_rhel is complete
        05:32:09  Replication enablement for volumes has started for VM vmrm_rhel
        05:32:18  Replication enablement for volumes has completed for VM vmrm_rhel
        05:32:18  Backup VM creation has started for VM vmrm_rhel
        05:32:18  Network Configuration has completed for VM vmrm_rhel
        05:32:38  Backup VM vmrm_rhel_BackUp creation has completed
        05:32:38  Backup VM configuration update has started for VM vmrm_rhel_BackUp
        05:32:58  Backup VM configuration update has completed for VM vmrm_rhel_BackUp
        05:32:58  Discovery for Workgroup vmrm_rhel_WG is complete
        05:32:58  Replication is going on in background. Please use "ksysmgr query Workgroup <wgname> status monitor=yes " to track the progress of the operation.
05:32:58  Discovery has finished for DAL
1 out of 1 managed VMs have been successfully discovered
```

## Workgroup discovery and resync example
{: #wdr}

### To discover a workgroup, run the following command:
{: #dwr}

```
ksysmgr discover workgroup <name>
      [monitor=<yes|no>]
discover => di*
workgroup => workg*, work_g*, wg
```

An output that is similar to the following example is displayed:

```
ksysmgr discover workgroup vmrm_rhel_WG
04:10:41  Running discovery on Workgroup vmrm_rhel_WG, this may take a few minutes...
        04:10:54  Discovery has started for Workgroup vmrm_rhel_WG
        04:10:54  Discovery has started for VM vmrm_rhel
        04:11:09  Discovery for VM vmrm_rhel is complete
        04:11:09  Replication enablement for volumes has started for VM vmrm_rhel
        04:11:12  Replication enablement for volumes has completed for VM vmrm_rhel
        04:11:12  Backup VM creation has started for VM vmrm_rhel
        04:11:12  Network Configuration has completed for VM vmrm_rhel
        04:11:43  Backup VM vmrm_rhel_BackUp creation has completed
        04:11:43  Backup VM configuration update has started for VM vmrm_rhel_BackUp
        04:12:05  Backup VM configuration update has completed for VM vmrm_rhel_BackUp
        04:12:05  Discovery for Workgroup vmrm_rhel_WG is complete
        04:12:05  Replication is going on in background. Please use "ksysmgr query Workgroup <wgname> status monitor=yes " to track the progress of the operation.
04:12:05  Discovery has finished for vmrm_rhel_WG
1 out of 1 managed VMs have been successfully discovered
```

### To resync a workgroup, run the following command:
{: #rwr}

```
ksysmgr [-f] resync workgroup <workgroup_name>
resync => resy*
workgroup => workg*, work_g*, wg
```

An output that is similar to the following example is displayed:

```
ksysmgr resync workgroup vmrm_testvm_WG
Workgroup vmrm_testvm_WG resync has started
        23:49:17  Shutdown has started for VM vmrm_testvm_BackUp
        23:49:34  Resync is in progress for Workgroup vmrm_testvm_WG
        23:49:34  Shutdown has completed for VM vmrm_testvm_BackUp
        23:50:56  Resync has completed for Workgroup vmrm_testvm_WG
```

## System query example
{: #sqe}

### To query the system, run the following command:
{: #qsre}

```
ksysmgr query system [ properties ]
query => q*, ls, get, sh*
system => sys*
```

An output that is similar to the following example is displayed:
```
ksysmgr query system
System-Wide Persistent Attributes
BaseUrl: test.cloud.test.com
Regions: us-east
dal10
api_key: #####1543D972B94F...
```
An output that is similar to the following example is displayed for private cloud:
```
ksysmgr query system
System-Wide Persistent Attributes
BaseUrl:                     cloud.ibm.com
SatelliteLocations:          satloc_dal_clp2joc20ppo19876n50 - satloc_dal_cq8884h20ifkvm7quss0
api_key:                     #####16854C578FDCCF26592381C053 28F37FF3F7C 28E5039 9E1E6 398A87C8A 329A867 EEAA22CD5AC 435A65DBFA0819E3FC0F7E3A68BB4
staticipenable:              default...
```

## VM query and refresh example
{: #qre}


### To query a virtual machine, run the following command:
{: #qvm}

```
ksysmgr query vm [vmname1|lparuuid1...]
      [state=manage|unmanage]
      [status [monitor=<no|yes>]]
query => q*, ls, get, sh*
vm => lp*, vm
```

An output that is similar to the following example is displayed:

```
ksysmgr query vm User_test
Name: User_test
UUID: 6aae01cd-0960-4c7e-b5bd-f274bcd53792
State: INIT
Status: ACTIVE
IPAddresses: 10.160.0.64
```

### To refresh a virtual machine, run the following command:
{: #rvm}

```
ksysmgr refresh vm <vmname>
refresh => ref*
vm => lp*, vm
```

An output that is similar to the following example is displayed:

```
ksysmgr refresh vm User_test
Refresh VM info completed successfully.
```

## Event query example
{: #eqe}

### To query events, run the following command:
{: #rfc}

```
ksysmgr query event [type=<error|warning|info>]
query => q*, ls, get, sh*
event => ev*
```

An output that is similar to the following example is displayed:

```
ksysmgr query event type=error
Event Name: DISCOVERY_FAILED
Event Type: error
Description: Discovery has failed.
```

## Script deletion example
{: #sde}

### To delete a script, run the following command:
{: #dsr}

```
ksysmgr delete script entity=<workgroup|site|vm>
script_name=<custom_script_name>
delete => de*, remove, rm, erase
script => scr*
```

An output that is similar to the following example is displayed:

```
ksysmgr delete script entity=site script_name=pre_discovery
KSYS site has been updated
```

## Target system type
{: #Tr-sy-ty}

You can optionally specify a target system type when configuring a backup VM. This attribute allows the backup VM to run on a system different from the source.  For example,  If the production VM runs on a Power10 server and the backup VM can run on  Power9 server.

> **Note**: Setting the target system type is currently not supported for PowerVS Private cloud.

To configure a backup VM to run on a specific target system type, run the following command, run the following command:

```ksysmgr manage vm test-syd targetsystemtype=s922```

The following example output is displayed:

```
ksysmgr manage vm test-1 targetsystemtype=s922
Refresh VMs list of Test-lon04 workspace started
Refresh VMs list of Test-lon04 workspace completed
Refresh Networks list of Test-lon04 workspace started
Refresh Networks list of Test-lon04 workspace completed

```

To modify a backup VM to run on a specific target system type, run the following command:

```ksysmgr modify vm test-syd targetsystemtype=e980```

The following example output is displayed:

```
ksysmgr modify vm test_syd04 targetsystemtype=e980
TargetSystemType e980 was found and modified successfully
```

>**Note**: Modifying target system type is allowed only before first discovery.

## Shared Processor Pool configuration
{: #s-pro-poo-confi}

### Enable shared processor pool for a virtual machine for Public and Private cloud
{: #es-pp-vm}

To reduce licensing costs and optimize resource usage, you can enable the shared processor pool for a virtual machine. Before assigning, you must create the shared processor pool in the target PowerVS workspace.

Run the following command on Orchestrator node to manage the VM, and assign it to a shared processor pool:

```ksysmgr manage vm <vmname> sharedprocpool=yes targetprocpool=<pool_name>```

The following example output is displayed:

```
date; ksysmgr manage vm test_vm sharedprocpool=yes targetprocpool=test_pool
Wed May 28 14:22:35 IST 2025 Refresh VMs list of test_workspace started
Workgroup test_vm_WG added successfully
For Vm test_vm attribute(s) ShareProcPoolEnable was successfully modified.
For Vm test_vm attribute(s) TargetProcPool was successfully modified.
```

> **Note**: Both `sharedprocpool=yes` and `targetprocpool=<pool_name>` are mandatory parameters.

### Modify shared processor pool settings for a virtual machine Public and Private cloud
{: #msp-pp-vm}

To apply shared processor pool settings after a VM is managed, run the following command:

```ksysmgr modify vm <vmname> sharedprocpool=yes targetprocpool=<pool_name>```

The following example output is displayed:

```
ksysmgr modify vm test_vm sharedprocpool=yes targetprocpool=test_pool
For Vm test_vm attribute(s) ShareProcPoolEnable was successfully modified.
For Vm test_vm attribute(s) TargetProcPool was successfully modified.
```

**Note**: Modifying shared processor pool is allowed only before first discovery.

### Verify shared processor pool assignment for Public and Private cloud
{: #vs-pp-a}

To confirm that the VM is assigned to a shared processor pool, run the following command:

```ksysmgr query vm <vmname>```

The following example output is displayed:

```
UUID:             12345678-1234-5678-9xxx-0123456789xx
Processors:       1
Memory_capacity:  4
SharedProcPool:   yes
TargetProcPool:   test_pool
```

### View backup VM configuration in PowerVS
{: #vb-vm-cpv}

To check the shared processor pool assignment and current resource configuration of the backup VM, run the following command:

```ibmcloud pi ins get <backup_vm_name>```

The following example output is displayed:

```
CPU Cores:               0.25
Memory:                  2
Processor Type:          shared
Shared Processor Pool:   test_pool
Shared Processor Pool ID: abcd1234-xxxx-yyyy-zzzz-abcdef123456
Status:                  SHUTOFF
```
This confirms that the VM is provisioned with reduced capacity and is associated with specified processor pool. 

### Resource reduction during site switchovers for Public and Private cloud
{: #rr-pp-vm}

When a source VM is configured with a shared processor pool and the backup VM is also assigned to a shared processor pool, then the system automatically adjusts resources during a site move.

- **During discovery or DR readiness**:If the shared processor pool is configured for the target site, the backup VM is created with minimum CPU and memory resources from that pool.
This helps minimize cost while maintaining DR readiness.

- **Move from home site to backup site**: If Shared processor pool is configured for target site and source vm is from shared processor pool, during DR Readiness, target backup vm will be initially created with minimum resources.During move from home site to backup site, source vm which will be shutdown will be reduced to minimum resource and target system will be increase to actually vm resource configuration.

> **Note**: If source vm is not from shared processor pool but target site shared processor pool is configured. During move the source vm capacity will not be reduced during shutdown. Where target system resource will be increase utilizing resource from given pool.

- **Move back from backup site to home site**: The VM’s resources are restored to the original configuration values. This automated resource optimization helps reduce licensing costs and ensures efficient utilization during disaster recovery operations.

- **DR Rehearsal**: If the shared processor pool is configured for the target site, the rehearsal VM is created using resources from the target shared processor pool.
The rehearsal VM also respects the target system type defined by the user.

### List shared processor pools for Public and Private cloud
{: #li-sh-pro-po}

To list all shared processor pools created under your account, run the following command:

```ibmcloud pi spp list```

The following example output is displayed:

Listing shared processor pools under account Test Account as user `test_user@www.xxx.xx`:
| ID                                   | Available Cores | Host group | Host ID | Name         | Reserved Cores | Allocated Cores | Status | Status Detail      |
|-------------------------------------|------------------|------------|---------|--------------|----------------|------------------|--------|---------------------|
| xxxx1234-5678-90ab-xxxx-1234567890ab | 5                | e980       | 36      | spp_pool_01  | 2              | 0.5              | active | shared processor   |
| 1234abcd-5678-xxxx-ef12-xxxxxef987654 | 5                | s922       | 36      | test_pool    | 2              | 0.5              | active | shared processor   |


> **Note**: KSYS does not create the shared processor pool. You must create it manually in the PowerVS workspace before you can assign the share processor pool to any virtual machine.


## DR Rehearsal
{: #dr-re-mo-wo-l}

If you want to use a different network for the DR rehearsal instance, you must specify a DR rehearsal–specific network while pairing the network by using the `dr_test=yes` flag. When a DR rehearsal move is triggered, the DR rehearsal instance that is created at the DR site receives an IP address from the network that is explicitly specified for the DR test operation.

If you do not explicitly configure a DR rehearsal–specific network, the DR rehearsal instance uses the same target network IP that is configured for the actual DR operation.

To configure network pairing for a DR rehearsal–specific network,run the following command:

```
Ksysmgr pair network <source_nw_name> pair =<target_nw_name> dr_test=yes
```
DR Rehearsal network pairing can be verified at query workspace:

```
(0) root @ pbrazos01-ksys01: /opt/IBM/ksys/powervs
# ksysmgr query workspace vmrm-dal12 ; ksysmgr query workspace powervs-dr-wdc06
Name:                vmrm-dal12
ID:                  1d6118b5-bd77-4100-a655-754453558d9d
Region:              dal12
Type:                off-premises
Family:              data-center
CRN:                 crn:v1:bluemix:public:power-iaas:dal12:a/fe3c2ccd058e407c81e1dba2b5c0e0d6:1d6118b5-bd77-4100-a655-754453558d9d::
Status:
Default_Partner:     powervs-dr-wdc06
staticIPEnable:      default
VMs:                 ksysnode_dishant, vmrm_IBMi1, vmrm_test03, vmrm_test01
                     vmrm_test02, VMRM_DEV_TEST2_BackUp, vmrm_test05, vmrm_test04
                     VMRM_DEV-3, VMRM_DEV-2, aix_pub_vm, ksysnode01
                     VMRM_DEV-1
Networks:            dal12-network01, public-192_168_198_80-29-VLAN_2070, dal12_network01
Network pair:        dal12_network01 - wdc06_network01 (Workspace: powervs-dr-wdc06)
                     dal12-network01 - dal12-network01 (Workspace: powervs-dr-wdc06)
RehersalNetworkPair: dal12_network01 - wdc06_network01 (Workspace: powervs-dr-wdc06)
                     dal12-network01 - dal12-network01 (Workspace: powervs-dr-wdc06)

Name:                powervs-dr-wdc06
ID:                  xx2f37ac-xxxx-4e13-xxxx-7a9ba511xxxx
Region:              wdc06
Type:                off-premises
Family:              data-center
CRN:                 crn:v1:bluemix:public:power-iaas:wdc06:a/fe3c2ccd058e407c81e1dba2b5c0e0d6:912f37ac-918d-4e13-866a-7a9ba511c047::
Status:
Default_Partner:     vmrm-dal12
staticIPEnable:      default
VMs:                 VMRM_DEV_TEST2, oracle_test01_BackUp, vmrm_test05_BackUp, glvm_wdc06
                     aix_pub_test, VMRM_DEV-1_BackUp, vmrm_IBMi1_BackUp
Networks:            test_network01, public-000_168_000_80-29-VLAN_2070, test-network01
Network pair:        wdc06_network01 - test_network01 (Workspace: test-dal12)
                     test-network01 - test-network01 (Workspace: test-dal12)
RehersalNetworkPair: test_network01 - test_network01 (Workspace: test-dal12)
                     test-network01 - test-network01 (Workspace: test-dal12)
```
When DR Rehearsal VM is created in ksysmgr query vm it should display IP of DR Test specific network. 

### Disaster Recovery (DR) rehearsal at workgroup level
{: #drr-ree-mov-wo-ll}

Disaster Recovery (DR) rehearsal at the Workgroup level allows administrators to validate failover readiness without impacting production workloads. The ksysmgr CLI supports DR rehearsal operations by enabling movement and cleanup of Workgroups across DR sites.

### View workgroup information
{: #ve-wo-in}

Run the following command to list the existing Workgroups and verify their status:

```ksysmgr query workgroup```

An output that is similar to the following example is displayed:

```
Name:                          test_WG
ID:                            4b03e8a0-xxxx-xxxx-xxxx-8bfa973e1fcb
VMs:                           test_vm
PartnerVM:                     test_Backup
State:                         READY_TO_MOVE
Dr Test State:                 DRTESTCLEANUP_COMPLETED
Priority:                      Medium
SkipAutoResync:                OFF
HomeWorkspace:                 test_workspace_siteA
BackupWorkspace:               test_workspace_siteB
ActiveWorkspace:               test_workspace_siteA
Networks:                      net_mgmt <-> net_mgmt
CGName:                        cgrp-4a3e-xxxx-xxxx-7c2b2f61d2c9
Name:                          test2_WG
ID:                            9a82b701-xxxx-xxxx-xxxx-f4ab0e3f70e0
VMs:                           test2_vm
PartnerVM:                     test2_Backup
State:                         READY_TO_MOVE
Dr Test State:                 INIT
Priority:                      Medium
SkipAutoResync:                OFF
HomeWorkspace:                 test_workspace_siteA
BackupWorkspace:               test_workspace_siteB
ActiveWorkspace:               test_workspace_siteA
Networks:                      net_mgmt <-> net_mgmt
CGName:                       cgrp-6f2d-xxxx-xxxx-22487ee0caaa
```

> **Note**: Ensure the Workgroup state is `READY_TO_MOVE` before initiating a DR rehearsal move.

### Identify site details
{: #id-si-d}

To determine the source and target sites for the rehearsal, run the following command:

```ksysmgr query site```

An output that is similar to the following example is displayed:

```
Name:                           TargetSite
Region:                         lon06
Workspaces:                     Test_workspace_lon06_new
ActiveWorkgroups:               test_01_WG
Name:                           HomeSite
Region:                         lon04
Workspaces:                     drawpclon-Lon04-power-workspace
                                Test_WS_LON_04
                                customwsLON04
ActiveWorkgroups:               test_WG
```
This confirms the correct site names for use in the move command.

An output that is similar to the following example is displayed for private cloud

```
Name:                           TargetSite
SatelliteLocations:             satloc_dal_clp2joc20ppo19876n50
Workspaces:                     SVT-SMALL-Q3.2-mano-GRS
ActiveWorkgroups:               test_01_WG
Name:                           HomeSite
SatelliteLocations:             satloc_dal_cq8884h20ifkvm7quss0
Workspaces:                     SVT_3Q2_XSPoD_25
ActiveWorkgroups:               test_WG
```

### Perform DR Rehearsal move
{: #pe-dr-re-mo}

Initiate the DR rehearsal move using the following command:

```
ksysmgr move workgroup -h
ksysmgr move workgroup <name>
       to=<site_name>
       [force=<true|false>]
       [dr_type=<planned|unplanned>]
       [dr_test=<yes|no>]
    move => mov*, mv, swi*
    workgroup => workg*, work_g*, wg
Note: dr_type=planned is the default
```

### Parameters
{: #para-me-ter}

- **to:** Target site name (e.g., `TargetSite`)


An output that is similar to the following example is displayed:

```
ksysmgr move workgroup test_WG to=TargetSite dr_test=yes

You are initiating a failover rehearsal across sites

Do you wish to proceed? `[y/n]`

`y`

04:36:27   Workgroup dr_test move started for test_WG to TargetSite, this may take a few minutes...
04:36:38    dr_test move has started for Workgroup test_WG
04:36:38    Rehearsal VM creation has started for VM test
04:37:34    Rehearsal VM test_Rehearsal creation has completed
04:38:16    VM Volumes clone with consistency has started for test_BackUp
04:38:56    VM Volumes clone with consistency has completed for test_BackUp
04:38:56    Network Configuration has started for VM test_Rehearsal
04:39:16    Network Configuration has completed for VM test_Rehearsal
04:39:17    Volumes attachment has started for VM test_Rehearsal
04:42:12    Volumes attachment has completed for VM test_Rehearsal
04:42:22   Boot up on TargetSite Site has started for VM test_Rehearsal
04:44:05   Boot up on TargetSite Site has completed for VM test_Rehearsal
04:44:23   dr_test move has completed for Workgroup test_WG
Workgroup dr_test move completed for Workgroup test_WG to TargetSite
```

### Viewing workgroup information
{: #ve-work-info}

Run the following command to list the existing Workgroups and verify their status:

`ksysmgr query workgroup`

An output that is similar to the following example is displayed:

```
Name:                       test_Rehearsal
UUID:                       xxxx
State:                      INIT
Dr Test State:              ACTIVE
SourceVM:                   test
ActiveVM:                   no
IPAddresses:                192.168.x.xxx
memory_capacity:            2
Processors:                 0.25
WorkSpace:                  Test_workspace_lon06_new
Networks:                   mgmt_net

Name:                       test_BackUp
UUID:                       fe30xx38-babx-480x-920x-7fafad07c7xx
State:                      DISCOVERED
Dr Test State:              SHUTOFF
Partner:                    test
CloneVM:                    test_Rehearsal
ActiveVM:                   no
IPAddresses:                192.168.x.xxy
memory_capacity:            0
Processors:                 0.25
WorkSpace:                  Test_workspace_lon06_new
Networks:                   mgmt_net

Name:                       test
UUID:                       98d4xx06-a2x9-45x1-968x-3c6fb53a5fxx
State:                      READY_TO_MOVE
Dr Test State:              ACTIVE_COMPLETED
Partner:                    test_Rehearsal
CloneVM:                    yes
ActiveVM:                   192.168.x.xxz
IPAddresses:                2
memory_capacity:            0
Processors:                 0.25
WorkSpace:                  Test_workspace_lon06_new
Networks:                   mgmt_net

Name:                       testtest_01_Backup
UUID:                       889fxx15-a5dx-476x-be4x-0fficexx9cxx
State:                      DISCOVERED
Dr Test State:              SHUTOFF
Partner:                    no
CloneVM:                    yes
ActiveVM:                   192.168.x.xxw
IPAddresses:                2
memory_capacity:            0
Processors:                 0.25
WorkSpace:                  dravyclon_lon04_power_workspace
Networks:                   mgmt_net
```
An output that is similar to the following example is displayed for private cloud:

```
Name:                       test_Rehearsal
UUID:                       xxxx
State:                      INIT
Dr Test State:              ACTIVE
SourceVM:                   test
ActiveVM:                   no
IPAddresses:                192.168.x.xxx
memory_capacity:            2
Processors:                 0.25
WorkSpace:                  SVT-SMALL-Q3.2-mano-GRS
Networks:                   net-30

Name:                       test_BackUp
UUID:                       fe30xx38-babx-480x-920x-7fafad07c7xx
State:                      DISCOVERED
Dr Test State:              SHUTOFF
Partner:                    test
CloneVM:                    test_Rehearsal
ActiveVM:                   no
IPAddresses:                192.168.x.xxy
memory_capacity:            0
Processors:                 0.25
WorkSpace:                  SVT-SMALL-Q3.2-mano-GRS
Networks:                   net-30

Name:                       test
UUID:                       98d4xx06-a2x9-45x1-968x-3c6fb53a5fxx
State:                      READY_TO_MOVE
Dr Test State:              ACTIVE_COMPLETED
Partner:                    test_Rehearsal
CloneVM:                    yes
ActiveVM:                   192.168.x.xxz
IPAddresses:                2
memory_capacity:            0
Processors:                 0.25
WorkSpace:                  SVT-SMALL-Q3.2-mano-GRS
Networks:                   net-30

Name:                       testtest_01_Backup
UUID:                       889fxx15-a5dx-476x-be4x-0fficexx9cxx
State:                      DISCOVERED
Dr Test State:              SHUTOFF
Partner:                    no
CloneVM:                    yes
ActiveVM:                   192.168.x.xxw
IPAddresses:                2
memory_capacity:            0
Processors:                 0.25
WorkSpace:                  SVT_3Q2_XSPoD_25
Networks:                   net-30
```

### Clean Up after DR Rehearsal at workgroup level
{: #cl-up-wg-le}

Once validation is complete, revert the rehearsal environment using by running the following command:

```
ksysmgr cleanup workgroup -h
ksysmgr [-f] cleanup workgroup <name>
      dr_test=<yes>
      [force=<true|false>]
    cleanup => clean*
    workgroup => workg*, work_g*, wg
```
An output that is similar to the following example is displayed:
```
ksysmgr cleanup workgroup test1 dr_test=yes
04:46:33 Workgroup dr_test cleanup started for test1, this may take a few minutes...
04:46:44 dr_test cleanup has started for Workgroup test1
04:46:44 VM Volumes clone with consistency delete has started for VM test2
04:46:44 VM Volumes clone with consistency delete has completed for VM test2
04:46:44 VM Removal has started for VM test2
04:48:45 VM Removal has completed for VM test2
04:48:45 dr_test cleanup has completed for Workgroup test1
```

> **Note**: This command resets the test environment and returns the Workgroup to its pre-test state.

## DR rehearsal move at site level
{: #dr-re-mo-si-le}


### Disaster Recovery (DR) rehearsal at site level
{: #drr-ree-mo-si-lee}

Disaster Recovery (DR) rehearsal at the Site level allows administrators to validate failover readiness across entire sites without impacting production workloads. The ksysmgr CLI supports DR rehearsal operations by enabling site movement and cleanup.

### View site information
{: #ve-si-info}

Run the following command to list the existing Sites and verify their details:

```ksysmgr query site```

An output similar to the following example is displayed:

```
Name:                                TargetSite
Region:                              lon06
Workspaces:                          Test_workspace_lon06_newActive
Workgroups:                          test_01_WG
Name:                                HomeSite
Region:                              lon04
Workspaces:                          dravpclon-Lon04-power-workspace
                                     Test_WS_LON_04 
                                     customwsLON04Active
Workgroups:                          test_WG
```
This confirms the correct site names for use in the move command.

An output similar to the following example is displayed for private cloud:
```
Name:                                TargetSite
SatelliteLocations:                  satloc_dal_clp2joc20ppo19876n50
Workspaces:                          SVT-SMALL-Q3.2-mano-GRS
Workgroups:                          test_01_WG
Name:                                HomeSite
SatelliteLocations:                  satloc_dal_cq8884h20ifkvm7quss0
Workspaces:                          SVT_3Q2_XSPoD_25
Workgroups:                          test_WG
```

### Perform DR rehearsal move at site level
{: #pe-for-dr-re-mo}

Initiate the DR rehearsal move using the following command:

```
ksysmgr move site -h
ksysmgr [-f] move site
    from=<sourcename>
    to=<sitename>
    [force=<true|false>]
    [dr_type=<planned|unplanned>]
    [dr_test=<yes|no>]
move => mov*, mv, swi*
Note: dr_type=planned is the default.
```

### Parameters
{: #pa-ra-meter}

- **from:** Source site name (e.g., `HomeSite`)  
- **to:** Target site name (e.g., `TargetSite`)


An output similar to the following example is displayed:

```
ksysmgr move site from=HomeSite to=TargetSite dr_test=yes
You are initiating a failover rehearsal across sites

Do you wish to proceed? [y/n]  

y

03:28:32 Site dr_test move started for TargetSite to HomeSite, this may take a few minutes...
03:28:32 dr_test move has started for Workgroup test_01_WG
03:29:37 Rehearsal VM creation has started for VM test
03:30:41 Rehearsal VM test_Rehearsal creation has completed
03:31:15 VM Volumes clone with consistency has started for test_BackUp
03:32:41 VM Volumes clone with consistency has completed for test_BackUp
03:33:55 Network Configuration has started for VM test_Rehearsal
03:34:11 Network Configuration has completed for VM test_Rehearsal
03:34:11 Volumes attachment has started for VM test_Rehearsal
03:35:55 Volumes attachment has completed for VM test_Rehearsal
03:35:59 Boot up on HomeSite Site has started for VM test_Rehearsal
03:35:59 Boot up on HomeSite Site has completed for VM test_Rehearsal
03:35:59 dr_test move has completed for Workgroup test_01_WG
Site dr_test move completed for Site TargetSite to HomeSite
```

### View managed VMs after DR rehearsal
{: #ve-man-vms}

Use the following command to list the managed VMs and verify their status:
```
ksysmgr query vm state=manage
```
An output similar to the following example is displayed:

```
Name:                              test_Rehearsal
UUID:                              5de7xxaf-e78x-48bx-a9bx-695b8a2c76xx
State:                             INIT
Dr Test State:                     ACTIVE
SourceVM:                          test
ActiveVM:                          no
IPAddresses:                       192.168.x.xxa
memory_capacity:                   2
Processors:                        0.25
WorkSpace:                         Test_workspace_lon06_new
Networks:                          mgmt_net

Name:                              test_BackUp
UUID:                              e6aexx89-2c7x-43bx-867x-669426d0c6xx
State:                             INIT
Dr Test State:                     ACTIVE
SourceVM:                          test
ActiveVM:                          no
IPAddresses:                       192.168.x.xxb
memory_capacity:                   0
Processors:                        0.25
WorkSpace:                         dravpclon-lon04-power-workspace
Networks:                          mgmt_net

Name:                              testtest_01_Backup
UUID:                              889fxx15-a5dx-476x-be4x-0fficexx9cxx
State:                             DISCOVERED
Dr Test State:                     SHUTOFF
Partner:                           test_Rehearsal
CloneVM:                           no
ActiveVM:                          no
IPAddresses:                       192.168.x.xxc
memory_capacity:                   2
Processors:                        0.25
WorkSpace:                         dravpclon-lon04-power-workspace
Networks:                          mgmt_net

Name:                              test
UUID:                              28b6xx75-07ex-487x-bb5x-5faedfdc78xx
State:                             READY_TO_MOVE
Dr Test State:                     ACTIVE
Partner:                           test_BackUp
CloneVM:                           test_Rehearsal
ActiveVM:                          yes
IPAddresses:                       192.168.x.xxd
memory_capacity:                    2
Processors:                         0.25
WorkSpace:                          Test_workspace_lon06_new
Networks:                           mgmt_net
```
An output similar to the following example is displayed for private cloud:

```
Name:                              test_Rehearsal
UUID:                              5de7xxaf-e78x-48bx-a9bx-695b8a2c76xx
State:                             INIT
Dr Test State:                     ACTIVE
SourceVM:                          test
ActiveVM:                          no
IPAddresses:                       192.168.x.xxa
memory_capacity:                   2
Processors:                        0.25
WorkSpace:                         SVT-SMALL-Q3.2-mano-GRS
Networks:                          net-30

Name:                              test_BackUp
UUID:                              e6aexx89-2c7x-43bx-867x-669426d0c6xx
State:                             INIT
Dr Test State:                     ACTIVE
SourceVM:                          test
ActiveVM:                          no
IPAddresses:                       192.168.x.xxb
memory_capacity:                   0
Processors:                        0.25
WorkSpace:                         SVT-SMALL-Q3.2-mano-GRS
Networks:                          net-30

Name:                              testtest_01_Backup
UUID:                              889fxx15-a5dx-476x-be4x-0fficexx9cxx
State:                             DISCOVERED
Dr Test State:                     SHUTOFF
Partner:                           test_Rehearsal
CloneVM:                           no
ActiveVM:                          no
IPAddresses:                       192.168.x.xxc
memory_capacity:                   2
Processors:                        0.25
WorkSpace:                         SVT-SMALL-Q3.2-mano-GRS
Networks:                          net-30

Name:                              test
UUID:                              28b6xx75-07ex-487x-bb5x-5faedfdc78xx
State:                             READY_TO_MOVE
Dr Test State:                     ACTIVE
Partner:                           test_BackUp
CloneVM:                           test_Rehearsal
ActiveVM:                          yes
IPAddresses:                       192.168.x.xxd
memory_capacity:                    2
Processors:                         0.25
WorkSpace:                          SVT-SMALL-Q3.2-mano-GRS
Networks:                           net-30
```

### Clean up after DR rehearsal at site level
{: #clean-up}

Once validation is complete, revert the rehearsal environment using:

```
ksysmgr cleanup site -h
ksysmgr cleanup site <sitename>
    dr_test=<yes>
cleanup => clean*
```
An output similar to the following example is displayed:
```
ksysmgr clean site test dr_test=yes
07:26:51 Site dr_test cleanup started for test, this may take a few minutes...
07:27:02 dr_test cleanup has started for Workgroup test_WG1
07:27:02 dr_test cleanup has started for Workgroup test_WG2
07:27:02 VM Removal has started for VM test_VM2_Rehearsal
07:27:03 VM Volumes clone with consistency delete has started for VM test_VM1_Rehearsal
07:27:03 VM Volumes clone with consistency delete has completed for VM test_VM1_Rehearsal
07:27:03 VM Removal has started for VM test_VM1_Rehearsal
07:28:45 VM Removal has completed for VM test_VM1_Rehearsal
07:28:50 dr_test cleanup has completed for Workgroup test_WG1
07:39:56 VM Removal has completed for VM test_VM2_Rehearsal
07:40:01 dr_test cleanup has completed for Workgroup test_WG2
Site dr_test cleanup has completed for Site test
```
> **Note**: This command resets the test environment and returns the Site to its pre-test state.
