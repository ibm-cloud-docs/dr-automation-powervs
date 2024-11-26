---
front_matter_title: "KSYS Commands"
lastupdated: "2024-10-23"
copyright: "2023, 2024"
subcollection: dr-automation
---
# ksysmgr command(Orchestrator)

The command provides a consistent interface to configure the controller system (KSYS) and to perform IBM® VM Recovery Manager DR operations by using a terminal or script.

## syntax

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

All ksysmgr command operations are logged in the ```/var/ksys/log/ksysmgr.oplog``` file, including the name of the executed command, start time, process ID for the ksysmgr operation, the command with arguments, and overall return code.

## ACTION

The ```ACTION``` flags are not case-sensitive. All ```ACTION``` flags provide a shorter alias. For example, ```rm``` is an alias for ```delete```. Aliases are provided for convenience from the command line and must not be used in scripts.

The following ```ACTION``` flags are available:

>Note: The asterisk ```(*)``` in the aliases signify wildcard characters. For example, for the modify ACTION, the alias value is ```modd```. If you type ```mod*```, the command still works.

```query (alias: q*, ls, get, sh*)```

```add (alias: ad*, create, cr*, make, mk, bu*, bld)```

```delete (alias: de*, remov*, rm, er*)```

```modify (alias: mod*, ch*, set, sets)```

```restore (alias: rest*)```

```manage (alias: man*, mg)```

```unmanage (alias: unman*, umg)```

```discover (alias: di*)```

```move (alias: mov*, mv, swi*)```

```pair (alias: map)```

```refresh```

## CLASS

Specifies the type of object on which the ```ACTION``` is performed. The ```CLASS``` flags are not case-sensitive.

The following ```CLASS``` objects are supported:

```ksyscluster (alias: cl*, ksyscl*)```

- ```site (alias: sit*)```

```vm (alias: lp*, vm*)```

```notify (alias: rn, remote_not*, noti*)```

```snapshot (alias: snap*)```

```script```

```workgroup```

```disk```

```event```

```system (alias: sys*)```

```workspace```

```network```

```region```

## NAME

Specifies the particular object, of type **CLASS** , on which the **ACTION** must be performed. The NAME flags are case-sensitive.

**ATTR=VALUE**

Specifies an optional flag that has attribute pairs and value pairs that are specific to the **ACTION** and **CLASS** combination. Use these pairs to specify configuration settings or to run particular operations. Both **ATTR** and **VALUE** flags are case-sensitive.

**```-a {<ATTR#1>,<ATTR#2>,...}```**

Displays only the specified attributes. This flag must be used with the query ACTION flag. For example:

```ksysmgr -a name,sitetype query site```

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

To get help information about the ksyscluster class, enter the following command:

```ksysmgr help ksyscluster```

An output that is similar to the following example is displayed:

```Available actions for ksyscluster: add delete modify query sync verify```

### Cluster configuration examples

#### To add a KSYS cluster:

```
ksysmgr add ksyscluster
[<ksysclustername>]
[type=<HA|DR|HADR|HADRHA|IBM_PVS_DR>]
ksysnodes=<ksysnode1[,ksysnode2,...]>
[sync=<yes|no>]
apikey=<apikey>
[baseurl=<baseurl>]
[proxy=<ipaddress:portnumber>]
add => ad*, cr*, make, mk
ksyscluster => ksysclu*, clu*

 **Note**: apikey, baseurl and proxy are applicable only for `IBM_PVS_DR cluster` 
```

An output that is similar to the following example is displayed:
```
Adding node to current cluster configuration
Ksyscluster has been created, running verify now
Ksyscluster has been verified, running sync now
Stopping KSYS subsystem ...
Starting KSYS subsystem ...
KSYS subsystem has started. You can begin adding site definitions, etc

**Note**: By default, the value of type variable is DR cluster type. 
```

#### To query the KSYS cluster:

```
ksysmgr query ksyscluster <ksysclustername>
query => q*, ls, get, sh*
ksyscluster => ksysclu*, clu*
```

An output that is similar to the following example is displayed:
```
Name: pvs_dr
State: Online
Type: IBM_PVS_DR
Ksysnodes: ksys804p.aus.stglabs.ibm.com:1:Online
KsysState: ksys804p.aus.stglabs.ibm.com:1:Online
```

#### To remove a KSYS cluster:

```
ksysmgr [-f] delete ksyscluster <ksysclustername>
delete => de*, remove, rm, erase
ksyscluster => ksysclu*, clu*
```

When you delete a KSYS cluster, the **ksysmgr** command prompts for your confirmation. The **ksysmgr** command also recommends to create a snapshot at this point. 

An output that is similar to the following example is displayed:
```
**WARNING**: This action will remove all configuration and destroy the KSYS setup. It's recommended to create a backup with "ksysmgr add snapshot -h"
```

Do you want a backup to be created now ? [y|n]

`y`
```
Taking snapshot...
Created: /var/ksys/snapshots/oldclust_DETAILED_2024-07-29_06:35:30.xml.tar.gz
Successfully created a configuration snapshot: /var/ksys/snapshots/oldclust_DETAILED_2024-07-29_06:35:30.xml.tar.gz
```

Do you wish to store the logs on successful cluster deletion? [y|n]

`y`

Do you wish to proceed? [y|n]

`y`

This may take a few minutes to remove the ksyscluster

The following log entries detail the process of stopping and removing various workgroups, along with the associated tasks:

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

#### To modify a KSYS cluster:

```
ksysmgr modify ksyscluster <ksysclustername> [glnode=<ksysnode>]
[add|remove]
[ksysnodes=<ksysnode1[,ksysnode2,...]>
[apikey=<apikey>]
[proxy=<ipaddress:portnumber>]
ksyscluster => ksysclu*, clu*
To check the version of the KSYS software:
ksysmgr query ksyscluster <ksysclustername>
query => q*, ls, get, sh*
ksyscluster => ksysclu*, clu*
Site configuration examples
```

#### To add a site in the KSYS subsystem:

```
ksysmgr add site <sitename> region=<regionname>
add => ad*
site => sit*
An output that is similar to the following example is displayed:
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

**Note**: dal10 partner GRS Region is us-east
```

#### To query the details about a specific sites:

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
ActiveWorkgroups: Maheshwari_WG, SivaKrishna_WG, vmrm_dev_01_WG

**Note**: Active means which site the VMs in host_group/workgroup are running, HG/WG are only active on one site at a time
```

By default, the replication type of the site is async.

#### To discover a site:

```
ksysmgr discover site <sitename>
discover => di*
site => sit*

The KSYS subsystem discovers all the hosts and virtual machines from all the host groups across both sites. The discovery operation might take a few minutes to a few hours to complete depending on the scale of the environment. By using the `-t` flag with the discover, verify, or move command, you can get timestamps for every step of progress.

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

**Note**: dal10 partner GRS Region is us-east
```

#### To delete a site:
```
ksysmgr delete site <sitename>
delete => de*, remove, rm, erase
site => sit*
```

An output that is similar to the following example is displayed:

```
ksysmgr del site us-east

**ERROR:** Deleting Site us-east is not allowed when workspace(s) vms are in managed state, unmanage following vms before deleting the site.

Maheshwari
ksysmgr del site us-east
Workspace VMRM-wdc was removed
Site us-east was removed
Workgroup configuration example
```

#### To move a workgroup from one site to another site, run the following command:

```
ksysmgr move workgroup <name>
to=<site_name>
[force=<true|false>]
[dr_type=<planned|unplanned>]
move => mov*, mv, swi*
workgroup => workg*, work_g*, wg
```

To query the details about a specific workgroup:
```
ksysmgr query workgroup [ name ]
[status [monitor=<no|yes>] | disk_group_view]
query => q*, ls, get, sh*
workgroup => workg*, work_g*, wg
```

An output that is similar to the following example is displayed: 

```
ksysmgr q wg Maheshwari_WG
Name: Maheshwari_WG
ID: 3
VMs: Maheshwari
State: INIT
Priority: Medium
SkipAutoResync: OFF
HomeWorkSpace: VMRM-wdc
BackupWorkSpace: VMRM-Dal10
ActiveWorkspace: VMRM-wdc
Networks: vmrm-wdc-network01<-> VMRM-Dal10-Network01
ksysmgr q wg Maheshwari_WG status monitor=yes
Workgroup Maheshwari_WG is currently in INIT state
Monitoring status...
Press Q to quit monitoring for activity.q.
ksysmgr q wg Maheshwari_WG disk_group_view
Name: Maheshwari_WG
CGName: rccg-04ac-d1bf0
CGState: consistent_copying
Progress: 99.0
```

##### To discover and verify all VMs in a specific work group:

```
ksysmgr discover workgroup <name>
[monitor=<yes|no>]
discover => di*
workgroup => workg*, work_g*, wg
```
An output that is similar to the following example is displayed: 

```
ksysmgr -t discover wg Maheshwari_WG
04:49:54 Running discovery on Workgroup Maheshwari_WG, this may take a few minutes...
04:49:55 Discovery has started for Workgroup Maheshwari_WG
04:49:55 Discovery has started for VM Maheshwari
04:49:55 Discovery for VM Maheshwari is complete
04:49:55 Replication enablement for volumes has started for VM Maheshwari
04:51:01 Replication enablement for volumes has completed for VM Maheshwari
04:51:01 Backup VM creation has started for VM Maheshwari
04:51:01 Network Configuration has completed for VM Maheshwari
04:51:47 Backup VM Maheshwari_BackUp creation has completed
04:51:52 Discovery for Workgroup Maheshwari_WG is complete
04:51:52 Replication is going on in background. Please use "ksysmgr query Workgroup status monitor=yes " to track the progress of the operation.
04:51:52 Discovery has finished for Maheshwari_WG
1 out of 1 managed VMs have been successfully discovered
```

##### To modify a workgroup:

ksysmgr modify workgroup <name>

[priority=<Low|Medium|High>]

[SkipAutoResync=<ON|OFF>]

workgroup => workg*, work_g*, wg

An output that is similar to the following example is displayed: 

ksysmgr modify workgroup <name>

[priority=<Low|Medium|High>]

[SkipAutoResync=<ON|OFF>]

workgroup => workg*, work_g*, wg

To resync a workgroup:

ksysmgr [-f] resync workgroup <workgroup_name>

resync => resy*

workgroup => workg*, work_g*, wg

An output that is similar to the following example is displayed: 

ksysmgr resync wg IBMiWG

Workgroup IBMiWG resync has started

05:24:38 Shutdown has started for VM neha_IBMi

05:24:54 Shutdown has completed for VM neha_IBMi

05:24:57 Resync is in progress for Workgroup IBMiWG

05:26:08 Resync has completed for Workgroup IBMiWG

LPAR configuration examples

To include or exclude a specific virtual machine from the KSYS configuration:

ksysmgr unmanage vm <vmname> | name=<vmname> | vmuuid=<uuid>

[workspace=<workspacename | ID>]

[force=<true|false>]

unmanage => unman*, umg

vm => lp*, VM

An output that is similar to the following example is displayed:

ksysmgr unmanage vm Maheshwari

07:16:47 Unmanage vm has started, this may take a few minutes...

07:16:53 Maheshwari_WG Workgroup stop VG has started

07:16:53 Maheshwari_WG Workgroup stop VG has completed

07:16:53 Removal of VG disks from Maheshwari_WG Workgroup has started

07:16:53 Removal of VG disks from Maheshwari_WG Workgroup has completed

07:16:53 Workgroup Maheshwari_WG was removed

VM Maheshwari was successfully unmanaged

The ksysmgr unmanage ALL host=<hostname> command will unmanage all virtual machines in the host <hostname>. The ksysmgr unmanage ALL host_group=HG1 command will unmanage all virtual machines in the host group HG1.

ksysmgr unmanage vm <vmname|lparuuid,....> unmanage => unman*, umg vm => lp*, vm

The preceding command syntax can be used for targeted VM management. The excluded virtual machine is not moved to the backup site when a site-switch operation is initiated.

Notes: Including or excluding a virtual machine, you must run the discovery and verification commands to rediscover the resources and validate the modified configuration setting.

To update the priority of virtual machines:

ksysmgr modify vm <vmname>

[targetsystem=<target_system_type>]

modify => mod*, ch*, set

vm => lp*, vm

Note: The display_all option can be used before performing the first discovery operation to display only minimum information about the VMs that are added to the KSYS configuration. To display the current information about a VM, use the ksysmgr query vm command without the display_all option.

Discovery and verification examples

To discover the resources in a site:

ksysmgr discover site <sitename>

discover => di*

site => sit*

An output that is similar to the following example is displayed:

ksysmgr -t discover site us-east

 

02:33:39  Running discovery on entire site, this may take a few minutes...

        02:33:49  Discovery has started for Workgroup Surendar_WG

        02:33:49  Discovery has started for Workgroup Maheshwari_WG

        02:33:50  Discovery has started for VM Surendar

        02:33:50  Discovery for VM Surendar is complete

        02:33:50  Replication enablement for volumes has started for VM Surendar

        02:33:50  Replication enablement for volumes has completed for VM Surendar

        02:33:50  Backup VM creation has started for VM Surendar

        02:33:50  Network Configuration has completed for VM Surendar

        02:33:50  Discovery has started for VM Maheshwari

        02:33:50  Discovery for VM Maheshwari is complete

        02:33:50  Replication enablement for volumes has started for VM Maheshwari

        02:33:50  Replication enablement for volumes has completed for VM Maheshwari

        02:33:50  Backup VM creation has started for VM Maheshwari

        02:33:50  Network Configuration has completed for VM Maheshwari

        02:34:01  Backup VM Surendar_BackUp creation has completed

        02:34:01  Backup VM Maheshwari_BackUp creation has completed

        02:34:01  Discovery for Workgroup Maheshwari_WG is complete

        02:34:01  Replication is going on in background. Please use "ksysmgr query Workgroup <wgname> status monitor=yes " to track the progress of the operation.

02:34:01  Discovery has finished for us-east

2 out of 2 managed VMs have been successfully discovered

Script configuration examples

To add a script for automatic execution before or after the discovery and verification operations:

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

Note: Network Configuration scripts are associated only with VM!

Note: The pre_verify and post_verify scripts can be run only at site level.

Events query examples

To query the event

ksysmgr query event [type=<error|warning|info>]

query => q*, ls, get, sh*

event => ev*

An output that is similar to the following example is displayed:

ksysmgr q event type=error

Current Notification Level: Low

Event Name Event Type Description

--------------------------------------------------------------------------------

DISCOVERY_FAILED error Discovery has failed.

MIGRATED_VM_EXISTS_IN_WG error Migrated vm exists in workgroup

DEPLOY_FAILED error Deploy vm has failed.

GRS_ENABLE_VOLUMES_FAILED error Volumes DR enablement has failed.

ONBOARD_VOLUMES_FAILED error Volumes onboard has succeeded.

ATTACH_VOLUMES_FAILED error Volumes attach has failed.

VM_SHUTDOWN_FAILED error VM shutdown has failed.

VM_BOOTUP_FAILED error VM bootup has failed.

REPLICATION_MONITOR_FAILED error Replication monitor has failed.

MOVE_FAILED error Move has failed.

VG_REVERSAL_FAILED error VG reversal has failed.

VG_STOP_FAILED error VG stop has failed.

VG_UPDATE_FAILED error VG update has failed.

VG_REMOVE_FAILED error VG remove has failed.

VG_REMOVE_DISKS_FAILED error VG remove disks has failed.

VM_REMOVE_FAILED error VM remove has failed.

VM_MISSED_FROM_WORKSPACE_PHASE error VM missed from the workspace

SCRIPT_FAILURE_EVENT error Script execution has failed.

ksysmgr q event type=warning

Current Notification Level: Low

Event Name Event Type Description

--------------------------------------------------------------------------------

NETWORK_CONFIGURATION_FAILED warning Network configuration has failed.

ksysmgr q event type=info

Current Notification Level: Low

Event Name Event Type Description

--------------------------------------------------------------------------------

DISCOVERY_STARTED info Discovery has started.

DISCOVERY_SUCCESS info Discovery has succeeded.

DEPLOY_STARTED info Deploy vm has started.

DEPLOY_SUCCESS info Deploy vm has succeeded.

GRS_ENABLE_VOLUMES_STARTED info Volumes DR enablement has started.

GRS_ENABLE_VOLUMES_SUCCESS info Volumes DR enablement has succeeded.

ONBOARD_VOLUMES_STARTED info Volumes onboard has started.

ONBOARD_VOLUMES_SUCCESS info Volumes onboard has failed.

ATTACH_VOLUMES_STARTED info Volumes attach has started.

ATTACH_VOLUMES_SUCCESS info Volumes attach has succeeded.

VM_SHUTDOWN_STARTED info VM shutdown has started.

VM_SHUTDOWN_SUCCESS info VM shutdown has succeeded.

VM_BOOTUP_STARTED info VM bootup has started.

VM_BOOTUP_SUCCESS info VM bootup has succeeded.

REPLICATION_MONITOR_STARTED info Replication monitor has started.

REPLICATION_MONITOR_SUCCESS info Replication monitor has succeeded.

MOVE_STARTED info Move has started.

MOVE_SUCCESS info Move has succeeded.

VG_REVERSAL_STARTED info VG reversal has started.

VG_REVERSAL_SUCCESS info VG reversal has succeeded.

VG_STOP_STARTED info VG stop has started.

VG_STOP_SUCCESS info VG stop has succeeded.

VG_UPDATE_STARTED info VG update has started.

VG_UPDATE_SUCCESS info VG update has succeeded.

VG_REMOVE_STARTED info VG remove has started.

VG_REMOVE_SUCCESS info VG remove has succeeded.

VG_REMOVE_DISKS_STARTED info VG remove disks has started.

VG_REMOVE_DISKS_COMPLETED info VG remove disks has succeeded.

VM_REMOVE_STARTED info VM remove has started.

VM_REMOVE_SUCCESS info VM remove has succeeded.

NETWORK_CONFIGURATION_STARTED info Network configuration has started.

NETWORK_CONFIGURATION_SUCCESS info Network configuration has succeeded.

SCRIPT_SUCCESS_EVENT info Script execution has succeeded.

NETWORK_CREATION_COMPLETED info Network creation has started.

To query the system-wide persistent attribute for the ksysmgr command, use the following command syntax:

ksysmgr query system [ properties ]

query => q*, ls, get, sh*

system => sys*

sysmgr q system

An output that is similar to the following example is displayed:

System-Wide Persistent Attributes

BaseUrl: test.cloud.ibm.com

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

Note: If the network_isolation attribute is set to ALL, the action attribute must have delete value. This will delete all the IP's.

To modify the system wide persistent attribute for the ksysmgr command:

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

An output that is similar to the following example is displayed:

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

Quick discovery example

To enable or disable the quick-discovery feature:

ksysmgr modify system quick_discovery_interval=6

To set the time duration for the quick-discovery operation:

KSYS quick_discovery_interval has been updated

Notification configuration examples

To add an email or SMS notification for a specific user:

ksysmgr add notify

user=<username>

contact=<contact>

ksysmgr add notify

script=<full path script>

event=<event name>

add => ad*, cr*, make, mk

notify => rn, remote_not*, noti*

Note: contact should be email address

An output that is similar to the following example is displayed:

ksysmgr add notify script=/surendar/a.sh event=DISCOVERY_STARTED successfully added script for event

To modify an email address or SMS number for a specific user:

ksysmgr modify notify

oldcontact=<user name | user email>

newcontact=<user name | user email>

ksysmgr modify notify

oldscript=<script>

newscript=<script>

modify => mod*, ch*, set

notify => rn, remote_not*, noti*

An output that is similar to the following example is displayed:

ksysmgr modify notify oldcontact=siva newcontact=sssssss

successfully modified user info

(0) root @ ksys804p: /

# ksysmgr q notify

Contact details:

User: sssssss

Contact: ssdhsadksa@gmail.com

Script details:

Script: /surendar/a.sh

Event: DISCOVERY_FAILED

Script: /surendar/a.sh

Event: DISCOVERY_STARTED

To query all the registered contact details:

ksysmgr query notify [ contact | script ]

[ user=<username> | contact=<contact> ]

[ script=<full path script> ]

query => q*, ls, get, sh*

notify => rn, remote_not*, noti*

An output that is similar to the following example is displayed:

ksysmgr query notify

Contact details:

User: siva

Contact: sitalu54@in.ibm.com

Script details: Script: /surendar/a.sh

Event: DISCOVERY_STARTED

To delete all the contact information for a specific user:

ksysmgr delete notify

user=<user name>

ksysmgr delete notify

script=<full path script> [ event=<event name> ]

delete => de*, remove, rm, erase

notify => rn, remote_not*, noti*

Note: User can give script name along with event name to remove notify for particular event.

Also, User can give Only script name to remove notify for all events listed with that script name

An output that is similar to the following example is displayed:

ksysmgr delete notify user="siva"

successfully deleted user info

To add a script for a predefined set of notifications and subsequent actions for a specific event:

ksysmgr add notify script=full_path_script event=event_name

For example,

ksysmgr add notify script=/surendar/a.sh event=DISCOVERY_STARTED successfully added script for event

To modify a script:

ksysmgr modify notify oldscript=old_file_name newscript=new_file_name

To remove a script:

ksysmgr delete notify

user=<user name>

ksysmgr delete notify

script=<full path script> [ event=<event name> ]

delete => de*, remove, rm, erase

notify => rn, remote_not*, noti*

Note: User can give script name along with event name to remove notify for particular event.

Also, User can give Only script name to remove notify for all events listed with that script name

To query a script:

ksysmgr query notify script

System-wide attributes configuration

To query details about system-wide attributes:

ksysmgr query system [ properties ]

query => q*, ls, get, sh*

system => sys*

An output that is similar to the following example is displayed:

ksysmgr q system

System-Wide Persistent Attributes

BaseUrl: test.cloud.ibm.com

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

To enable the KSYS subsystem to rediscover the resources at noon every day automatically:

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

An output that is similar to the following example is displayed:

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

To change the notification level of your system to receive notification for all critical errors and warnings of all events:

ksysmgr modify system notification_level=medium

To change the duplicate event processing option to receive notification for all events, even if the events are duplicated:

ksysmgr modify system dup_event_processing=no
