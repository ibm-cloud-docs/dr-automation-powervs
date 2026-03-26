---
copyright:
  years: 2025
lastupdated: "2026-03-26"

subcollection: dr-automation-powervs

keywords: create instance for PowerHA , powerha instance, add node

---

# Creating HA cluster
{: #creating-ha-cluster}


## Create HA cluster
{: #create-ha-cluster}

After creating the service instance, configuring the HA cluster in {{site.data.keyword.DR_full}} is required to enable high availability for your Power Virtual Server environment. The HA cluster establishes coordinated nodes that help ensure workload continuity during planned or unplanned outages. This screen allows you to configure the location, workspace, API authentication key, and related high availability settings. Once configured, {{site.data.keyword.DR_short}} supports automatic failover and resilient operations to maintain service availability.
{:shortdesc: .shortdesc}

### Procedure
{: #procedure-ha-cluster}

To configure the HA cluster, complete the following steps:

1. On the **Service details** page, in the **HA cluster** section, click **Edit**.
2. In the **Edit configuration** panel, enter the required **API key** and validate it.
3. Select the **High availability location**.
4. Select the appropriate **Power Virtual Server workspace**.
5. Click **Save** to apply the configuration.

## Add Node
{: #add-node}

After you complete the HA cluster configuration, add nodes to the cluster.

### Procedure
{: #procedur-add-node}

To add nodes, complete the following steps:

1. On the **Service details** page, scroll to the **Cluster nodes** section.
2. Click **Add node**.
3. In the **Add nodes** panel, review the following details:
   - **High availability location**
   - **Power Virtual Server workspace name**
   - **Power Virtual Server workspace ID**

4. From the list of available virtual server instances, select the nodes that you want to add to the cluster.
   You can review details such as:
   - **Name**
   - **ID**
   - **IPs**
   - **Cores**
   - **Memory**
   - **Status**

5. Click **Add instance** to add the selected nodes to the cluster.

6. If there are no virtual servers instance added ,complete the following step.
Click **Naviagation Menu** > **Infratructer** > **Power Virtual Server** > **Workspace** > **Create a Wrokspace**.

After the nodes are added, they appear in the **Cluster nodes** table, where you can monitor their status and continue with agent installation and failover configuration.

## Download agent
---
copyright:
  years: 2025
lastupdated: "2026-03-26"

subcollection: dr-automation-powervs

keywords: create instance for PowerHA , powerha instance, add node
---

# Creating HA cluster
{: #creating-ha-cluster}

## Create HA cluster
{: #create-ha-cluster}

After creating the service instance, configuring the HA cluster in {{site.data.keyword.DR_full}} is required to enable high availability for your Power Virtual Server environment. The HA cluster establishes coordinated nodes that help ensure workload continuity during planned or unplanned outages.
{:shortdesc: .shortdesc}

### Procedure
{: #procedure-ha-cluster}

1. On the **Service details** page, in the **HA cluster** section, click **Edit**.
2. Enter the required **API key** and validate it.
3. Select the **High availability location**.
4. Select the **Power Virtual Server workspace**.
5. Click **Save**.

---

## Add node
{: #add-node}

After configuring the HA cluster, add nodes to the cluster.

### Procedure
{: #procedure-add-node}

1. On the **Service details** page, go to the **Cluster nodes** section.
2. Click **Add node**.
3. Review the following details:
   - High availability location  
   - Power Virtual Server workspace name  
   - Power Virtual Server workspace ID  
4. Select the virtual server instances that you want to add.
5. Click **Add instance**.


## Download agent
{: #download-agent}

After adding nodes, download and install the agent on each virtual machine (VM). The agent enables communication with {{site.data.keyword.DR_short}} and is used to manage PowerHA operations such as installation, upgrade, uninstallation, and registration.
{:shortdesc: .shortdesc}

### Procedure
{: #procedure-download-agent}

1. On the **Service details** page, go to the **Cluster nodes** section.
2. Click **Download agent**.

   The agent fileset (`powerha-agent.rte`) is downloaded to your local system.

3. Copy the downloaded fileset to each VM that is added to the cluster.

4. Log in to each VM and install the fileset by using the `installp` command.

5. After installation, go to the agent installation directory:

```bash
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

Note: Ensure API_KEY and SERVICE_INSTANCE_ID are exported as environment variables when arguments are not passed
```


### List supported PowerHA versions
{: #list-powerha-versions}

```bash
./powerha-agent -l
```

Example output:

```text
INFO: API_KEY and SERVICE_INSTANCE_ID are not provided as arguments, continuing with environment variables...
INFO: Starting PowerHA Agent...
INFO: Fetching supported PowerHA versions...
INFO: PowerHA supported versions:

- 7210SP1
- 729SP1
- 728SP3
- 727SP3

INFO: Agent job is Completed
```


### Set authentication parameters
{: #set-authentication}

```bash
export API_KEY=<value>
export SERVICE_INSTANCE_ID=<value>
```
### Install PowerHA
{: #install-powerha}

To install a PowerHA version on the VM, run:

```bash
./powerha-agent -i API_KEY=<value> SERVICE_INSTANCE_ID=<value> PHA_VERSION=<value>
```

Alternatively, if the API key and service instance ID are set as environment variables:

```bash
./powerha-agent -i PHA_VERSION=<value>
```

Example:

```bash
./powerha-agent -i PHA_VERSION=729SP1
```

Example output:

```text
Starting PowerHA Agent...
Performing pre-validation...
Fetching supported PowerHA versions...
PowerHA version '729SP1' is supported for the deployment
Checking whether PowerHA is already installed or not...
PowerHA is not installed on this system
Checking disk space...
Available disk space in root filesystem: 2.04 GB
Available disk space in user filesystem: 5.39 GB
Sufficient space is available to install the PowerHA
Starting download, extraction, and installation process...
Downloading PowerHA file for VM: phametering, Version: 729SP1
Successfully downloaded PowerHA version 729SP1 for VM: phametering
Extracting file: 729SP1.tar.gz
Successfully extracted the tar file
Installing AIX filesets...
Installing PowerHA filesets...
Successfully installed PowerHA filesets from: /729SP1/inst.images
Installing PowerHA SP filesets...
Successfully installed PowerHA SP filesets from: /729SP1/update.images
Cleaning up temporary files
Performing post-installation validations...
Agent job is Completed
```

### Uninstall PowerHA
{: #uninstall-powerha}

```bash
./powerha-agent -u
```

### Upgrade PowerHA
{: #upgrade-powerha}

```bash
./powerha-agent -ug PHA_VERSION=<value>
```

### Register existing PowerHA
{: #register-powerha}

```bash
./powerha-agent -r
```

Force register:

```bash
./powerha-agent -r -f
```


### Monitoring status in the UI
{: #agent-status}

The **Cluster nodes** table displays:

- Agent status  
- PowerHA version  

Example values:

- AGENT_DOWNLOAD_REQUIRED  
- AGENT_DOWNLOADED  
- POWERHA_FILESETS_DOWNLOAD_STARTED  
- POWERHA_INSTALLATION_COMPLETED  
- FAILED  

### Next steps
{: #next-steps-ha}

After the agent installation is complete:

- The node status is updated in the **Cluster nodes** table with the corresponding PowerHA installation state.

- The **PowerHA version** and **Agent status** fields are updated for the node.

- Events are generated and recorded in the **Events** section of the service instance.

  These events provide details about the PowerHA installation activity and status for each node.
