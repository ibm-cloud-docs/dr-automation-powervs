---
copyright:
  years: 2025
lastupdated: "2026-04-22"

subcollection: dr-automation-powervs

keywords: create instance for PowerHA , powerha instance, add node, download agent

---

# Deploying the PowerHA SystemMirror
{: #deploying-ha-systemirror}


After the service instance is created, deploy PowerHA SystemMirror for IBM Power Virtual Server to enable high availability for your environment. This deployment establishes coordinated nodes that help ensure workload continuity during planned or unplanned outages.

During the deployment, you can select the region and workspace where your Power Virtual Server instances are located. After selecting the region and workspace, submit the configuration. Once submitted, the Add Node panel allows you to choose the available virtual server instances on which to enable PowerHA SystemMirror for your applications.

{:shortdesc: .shortdesc}

## Procedure
{: #procedure-ha-cluster}

To configure the HA deployment, complete the following steps:

1. In the **Service details** page, in the **HA cluster** section, click **Edit**.
2. In the **Edit configuration** page, enter the required **API key** and it validates the API key.
3. Select the **High availability location**.
4. Select the appropriate **Power Virtual Server workspace**.
5. Click **Submit** to apply the configuration.

## Add Node
{: #add-node}

After you complete the HA deployment configuration, add nodes to the deployment.To add nodes follow the instruction:


### Procedure
{: #procedur-add-node}

To add nodes, complete the following steps:

1. On the **Service details** page, scroll to the **Cluster nodes** section.
2. Click **Add node**.
3. In the **Add nodes** page, review the following details that you have already provided in the earlier step:
   - **High availability location**
   - **Power Virtual Server workspace name**
   - **Power Virtual Server workspace ID**

4. From the list of instances, you can select only that are in an active state, with a maximum of eight nodes supported for deployment. You can review the following details:
   - **Name**
   - **ID**
   - **IPs**
   - **Cores**
   - **Memory**
   - **Status**

5. Click **Add instance** to add the selected nodes to the cluster.

After the nodes are added, they appear in the **Cluster nodes** table, where you can monitor their status and continue with agent installation and failover configuration.

Once the all the nodes are configured, you can enable the PowerHA cluster configuration that supports failover and resilient operations to maintain the application high availability. 

## Download agent
{: #download-agent}

After adding the nodes to the PowerHA cluster, download the agent. The agent downloads and installs the required PowerHA SystemMirror version on each node and prepares them for cluster configuration.

{:shortdesc: .shortdesc}

### Procedure
{: #procedure-download-agent}

1. On the **Service details** page, go to the **Cluster nodes** section.
2. Click **Download agent**.

   The agent file set (`powerhaagent.rte`) is downloaded to your local system.

3. Copy the downloaded file set to each VM that is added to the cluster.

4. Log in to each VM and install the file set by using the `smit` or `installp` command.

5. After installation, go to the agent installation directory:

  ```
  /opt/IBM/powerha-agent/
  ```

6. Verify that the agent is installed:

  ```bash
  ./powerha-agent -h
  ```

Example output:

```text
PowerHA Agent CLI - Manage PowerHA installation on this system

Usage:
  ./powerha-agent COMMAND [[API_KEY=<value> SERVICE_INSTANCE_ID=<value>]
       [PHA_VERSION=<value>]] [DOWNLOAD_DIR=<path>]

Commands:
  -h, --help       Show this help message and exit.
  -l, --list       List all PowerHA versions supported by the deployment.
  -i, --install    Install the specified PowerHA version.
                   Requires: PHA_VERSION=<value>
  -u, --uninstall  Uninstall the currently installed PowerHA version.
  -ug, --upgrade   Upgrade the current PowerHA version.
                   Requires: PHA_VERSION=<value>
  -r, --register   Register an existing PowerHA version present on this node.

Options:
  -f, --force      Force registration even if the installed version is not supported.
                   (Only used with -r / --register)

Optional parameters:
  API_KEY=<value>
  SERVICE_INSTANCE_ID=<value>
  PHA_VERSION=<value>
  DOWNLOAD_DIR=<path>

Example: powerha-agent -i API_KEY=abc123xyz34adf SERVICE_INSTANCE_ID=fgg34xy224adfa46 PHA_VERSION="7.2.8 SP4" DOWNLOAD_DIR=/tmp

Note: Ensure API_KEY and SERVICE_INSTANCE_ID are exported as environment variables when arguments are not passed
```

## List supported PowerHA versions
{: #list-powerha-versions}

```bash
./powerha-agent -l
```

Example output:

```text
bash-5.2# /opt/IBM/powerha-agent/powerha-agent -l
INFO: API_KEY and SERVICE_INSTANCE_ID are not provided as arguments, continuing with environment variables...
INFO: Starting PowerHA Agent...
INFO: Fetching supported PowerHA versions...
INFO: PowerHA supported versions:
 - 7.2.10 SP1
 - 7.2.9 SP2
 - 7.2.8 SP4
INFO: Agent job is Completed
```


## Set authentication parameters
{: #set-authentication}

```bash
export API_KEY=<value>
export SERVICE_INSTANCE_ID=<value>
```

## Install PowerHA
{: #install-powerha}

To install PowerHA, ensure that you have 3 GB of available space in the `DOWNLOAD_DIR` path or the `$HOME` path, and 2 GB of available space in the `/usr` filesystem.

To install a PowerHA version on the VM, run:

```bash
./powerha-agent -i API_KEY=<value> SERVICE_INSTANCE_ID=<value> PHA_VERSION=<value>
```

Alternatively, if the API key and service instance ID are set as environment variables:

```bash
./powerha-agent -i PHA_VERSION=``7.2.9 SP2`` DOWNLOAD_DIR=/home
```

Example:

```bash
./powerha-agent -i API_KEY=<value> SERVICE_INSTANCE_ID=<value> PHA_VERSION=<value> DOWNLOAD_DIR=<value>
```

Example output:

```text
bash-5.2# /opt/IBM/powerha-agent/powerha-agent -i PHA_VERSION=``7.2.9 SP2`` DOWNLOAD_DIR=/home/temp
INFO: API_KEY and SERVICE_INSTANCE_ID are not provided as arguments, continuing with environment variables...
INFO: Starting PowerHA Agent...
INFO: Performing pre-validation...
INFO: Fetching supported PowerHA versions...
INFO: PowerHA version 7.2.9 SP2 is supported for the deployment.
INFO: Checking whether PowerHA is already installed or not...
INFO: PowerHA is not installed on this system.
INFO: Checking disk space...
INFO: Available disk space in /home/temp filesystem: 3.03 GB
INFO: Available disk space in /usr filesystem: 3.85 GB
INFO: Sufficient space is available to install PowerHA on the VM.
INFO: Starting download  extraction  and installation process...
INFO: Downloading PowerHA file for VM: powerha-agent  Version: 7.2.9 SP2
[==================================================]   100.0%  780.88 MB / 780.88 MB  19.75 MB/s  ETA --:--
Download complete: 780.88 MB at avg 19.75 MB/s
INFO: Successfully downloaded PowerHA version.
INFO: Extracting PowerHA files...
INFO: Successfully extracted PowerHA files.
INFO: Installing AIX filesets...
INFO: Successfully installed AIX filesets.
INFO: Installing PowerHA filesets...
INFO: Successfully installed PowerHA filesets.
INFO: Installing PowerHA SP filesets...
INFO: Successfully installed PowerHA SP filesets.
INFO: Cleaning up temporary files...
INFO: Successfully cleaned up temporary files.
INFO: Performing post-installation validations...
INFO: Installed PowerHA SystemMirror version is 7.2.9 SP2
INFO: Agent job is Completed
```

## Uninstall PowerHA
{: #uninstall-powerha}

```bash
./powerha-agent -u
```

## Upgrade PowerHA
{: #upgrade-powerha}

```bash
./powerha-agent -ug PHA_VERSION=<value>
```

## Register existing PowerHA
{: #register-powerha}

```bash
./powerha-agent -r
```

Force register:

```bash
./powerha-agent -r -f
```

## Monitoring status in the UI
{: #agent-status}

The **Cluster nodes** table displays:

- Agent status  
- PowerHA version  

Example values:

  - Agent download required
  - Agent downloaded
  - Powerha filesets download started
  - Powerha filesets download failed
  - Powerha filesets download completed
  - Powerha installation started
  - Powerha installation failed
  - Powerha installation completed
  - Powerha migration started
  - Powerha migration failed
  - Powerha migration completed
  - Powerha uninstallation started
  - Powerha uninstallation failed
  - Powerha uninstallation completed

## Next steps
{: #next-steps-ha}

After the agent installation is complete:

- The node status is updated in the **Cluster nodes** table with the corresponding PowerHA installation state.

- The **PowerHA version** and **Agent status** fields are updated for the node.
