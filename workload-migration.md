---

copyright:
  years: 2025
lastupdated: "2025-10-10"

subcollection: dr-automation

keywords: migration, migration deployment , upgrade, upgrade your deployment, snapshot

---

# Backing up and restoring the configuration data of KSYS in {{site.data.keyword.DR_full}}
{: #plan-work-load}

When workloads are deployed on a new system, you must pay attention to its configuration and tuning to achieve the expected performance. {{site.data.keyword.DR_full_notm}} uses different IBM Power Systems: S922, E980, E1080, S1022, E1080, E1050 and S1122.
{:shortdesc: .shortdesc}

For more information on hardware specifications that you might need, see [Hardware specifications for {{site.data.keyword.DR_full_notm}}](/docs/dr-automation-powervs?topic=dr-automation-powervs-arch#hs).

For AIX, {{site.data.keyword.DR_full_notm}} supports only AIX 7.3, or later. If you use an unsupported version, it is subject to outages during planned maintenance windows with no advanced notification given. Your current AIX level and POWER processor family can help determine which migration path to follow.

## Migration Statergies
{: #mig-ra-tion}

This section provides a high-level walkthrough for upgrading your existing deployment to the latest supported version. It outlines the essential steps for taking a snapshot from the source environment, restoring it on a new deployment, and completing the transition cleanly.

Check the current Orchestrator version by running the follwoing command:

```ksysmgr query version```

This display the current version number. Based on the version, choose one of two methods to migrate:

- [Migrate using snapshot backup and restore](#migrate-using-snapshot-backup-and-restore): If the current version is older than `1.9.0.1`. This involves taking a configuration snapshot on the source and restoring it onto a new deployment.
- [Migrate using direct approach](#migration-using-direct-approach): If the current version is `1.9.0.1` or later. This upgrades the existing deployment using the `ksysmgr upgrade file set` command.

## Migrate using snapshot backup and restore
{: #snapshot-mig}

To Migrate your current orchestrator to the latest version, complete the following steps:

1. Identify the Orchestrator from the workspace for your deployment.

2. Login in to the Orchestrator VM.

3. Check the current version of your Orchestrator using the following command:

   ```
   ksysmgr query version
   ```

   An output that is similar to the following example is displayed:

   ```
   Ksysmgr version: 1.8.0.0
   Ksys version: 1.8.0.0
   ```

   

4. Take a snapshot on your deployment from the Orchestrator by running the following command:

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

6. Now upload the snapshot manually to the IBM COS bucket.(if the version is 1.8.0.1)
 > note:If your at 1.9.0.0 version , you can take snapshot and directly upload it to COS,using the follwoing command:
 ```ksysmgr add snapshot <filepath> upload_to_cos```

 The following is the output :
 ```
 
 ```

### Migration using direct approach
{: #snapshot-dir-ap}

1. Create a new deployment where your Orchestator is deployed with newer version.

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
