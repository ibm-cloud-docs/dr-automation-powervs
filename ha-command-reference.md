---
copyright:
  years: 2026
lastupdated: "2026-03-25"

keywords: powerhaautomation service, cli, plugin

---

# PowerHA CLI commands
{: #powerha-cli-version}

## Available commands
{: #powerha-available-commands}
`api-key` - Manage the API key for the PowerHA Automation service instance.  
`cluster-node` - Manage PowerHA cluster nodes including add, get, and delete operations.  
`deployment` - Manage PowerHA deployment lifecycle including create and get operations.  
`event` - View events generated during PowerHA operations.  
`agent` - Download PowerHA agent and track download status.  
`powervs-workspaces` - Retrieve PowerVS workspaces for the specified service instance.  
`locations` - List supported PowerVS locations for PowerHA.  
`last-operation` - Retrieve the most recent operation details for the service instance.

## Api Key
{: #power-hadr-api-key-cli}

Manage apikey.

```sh
ibmcloud power-hadr powerhasm api-key --help
```

```
NAME:
  api-key - Manage apikey.

USAGE:
  ibmcloud power-hadr powerhasm api-key [action]

COMMANDS:
  update   Update apikey for the specified PowerHA service instance.

GLOBAL OPTIONS:
  -h, --help    Show help
  -q, --quiet   Suppresses verbose messages.

Use "ibmcloud power-hadr powerhasm api-key <command> --help" for more information about a command.

```

### `ibmcloud power-hadr powerhasm api-key update`
{: #power-hadr-cli-api-key-update-command}

Updates a new apikey for the specified PowerHA service instance.

```sh
ibmcloud power-hadr powerhasm api-key update --instance-id INSTANCE-ID [--api-key API-KEY] [--accept-language ACCEPT-LANGUAGE]
```


#### Command options
{: #power-hadr-api-key-update-cli-options}

`--instance-id` (string)
:   Unique identifier of the provisioned instance. Required.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9-]+$/`.

`--api-key` (string)
:   The API key to be stored or registered.

    The maximum length is `2048` characters. The minimum length is `1` character. The value must match regular expression `/^[A-Za-z0-9._:-]+$/`.

`--accept-language` (string)
:   The language requested for the return document.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

#### Example
{: #power-hadr-api-key-update-examples}

```sh
ibmcloud power-hadr powerhasm api-key update \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --api-key adfadfdsafsdfdsf \
    --accept-language en-US
```
{: pre}

### Example output
{: #power-hadr-api-key-update-cli-output}

```

Description   Key is valid.
Status        Key Updated Successfully
```


## Cluster Node
{: #power-hadr-cluster-node-cli}

Manage the PowerHA cluster node configuration, options to add PowerVS node to PowerHA configuration, fetch and delete the existing PowerHA node details.

```sh
ibmcloud power-hadr powerhasm cluster-node --help
```


### `ibmcloud power-hadr powerhasm cluster-node get`
{: #power-hadr-cli-cluster-node-get-command}

Retrieves details of all cluster nodes configured for the given PowerHA service instance.

```sh
ibmcloud power-hadr powerhasm cluster-node get --instance-id INSTANCE-ID [--if-none-match IF-NONE-MATCH]
```

### Command options
{: #power-hadr-cluster-node-get-cli-options}

`--instance-id` (string)
:   Unique identifier of the provisioned instance. Required.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9-]+$/`.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

### Example
{: #power-hadr-cluster-node-get-examples}

```sh
ibmcloud power-hadr powerhasm cluster-node get \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --if-none-match abcdef
```
{: pre}

### Example output
{: #power-hadr-cluster-node-get-cli-output}

```

ID                       crn:v1:staging:public:power-dr-automation:us-south:a/123333:123::
Primary Node Details
                         Agent Status   Powerha installation completed
                         Cores          0.5
                         IP Addresses   10.0.0.1
                         Memory         5
                         Pha Level      728SP4
                         Region         osa21
                         VM ID          f35327d7-4463-43dc-82ef-b63b1c19000
                         VM Name        TestVM1
                         VM Status      ACTIVE
                         Workspace ID   e03d1b8d-1cc1-4842-bf9e-9088282

Secondary Node Details   -
```
{: screen}

### `ibmcloud power-hadr powerhasm cluster-node add`
{: #power-hadr-cli-cluster-node-add-command}

Adds a new node to the PowerHA cluster for the specified PowerHA service instance.

```sh
ibmcloud power-hadr powerhasm cluster-node add --instance-id INSTANCE-ID --primary-cluster-nodes PRIMARY-CLUSTER-NODES [--secondary-cluster-nodes SECONDARY-CLUSTER-NODES] [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH]
```


#### Command options
{: #power-hadr-cluster-node-add-cli-options}

`--instance-id` (string)
:   Unique identifier of the provisioned instance. Required.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9-]+$/`.

`--primary-cluster-nodes` ([]string)
:   List of primary cluster node VM IDs. Required.

    The list items must match regular expression `/^[a-zA-Z0-9._:-]+$/`. The maximum length is `100` items. The minimum length is `1` item.

`--secondary-cluster-nodes` ([]string)
:   List of secondary cluster node VM IDs.

    The list items must match regular expression `/^[a-zA-Z0-9._:-]+$/`. The maximum length is `100` items. The minimum length is `0` items.

`--accept-language` (string)
:   The language requested for the return document.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

### Example
{: #power-hadr-cluster-node-add-examples}

```sh
ibmcloud power-hadr powerhasm cluster-node add \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --primary-cluster-nodes ede4c36e-002c-48da-992e-6039d230c478,ede4c36e-002c-48da-992e-6039d230c478 \
    --secondary-cluster-nodes ede4c36e-1234-48da-992e-6039d230c478,ede4c36e-1234-48da-992e-6039d230c478 \
    --accept-language en-US \
    --if-none-match abcdef
```
{: pre}

### Example output
{: #power-hadr-cluster-node-add-cli-output}

```

ID                       crn:v1:staging:public:power-dr-automation:us-south:a/8fd34108ddcf45e6a38adeb6a9d85e2c:e19e1de1-ab9f-46e6-aa1
                         5-77a7ac0f6eda::
Primary Node Details
                         Agent Status   Agent download required
                         Cores          0.25
                         IP Addresses   10.200.0.33
                         Memory         2
                         Region         us-south
                         VM ID          7a06d387-dcf8-4b88-a67f-bd9e3b8b89b1
                         VM Name        VM1
                         VM Status      ACTIVE
                         Workspace ID   30efa804-1364-43c1-b91c-123444444

Secondary Node Details   -

```
{: screen}

### `ibmcloud power-hadr powerhasm cluster-node delete`
{: #power-hadr-cli-cluster-node-delete-command}

Removes the specified cluster node from the PowerHA service instance.

```sh
ibmcloud power-hadr powerhasm cluster-node delete --instance-id INSTANCE-ID --vm-id VM-ID [--if-none-match IF-NONE-MATCH]
```


#### Command options
{: #power-hadr-cluster-node-delete-cli-options}

`--instance-id` (string)
:   Unique identifier of the provisioned instance. Required.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9-]+$/`.

`--vm-id` (string)
:   vm ID of workspace. Required.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9-]+$/`.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

#### Example
{: #power-hadr-cluster-node-delete-examples}

```sh
ibmcloud power-hadr powerhasm cluster-node delete \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --vm-id r006-2f3b3ab9-2149-49cc-83a1-30a5d93d59b2 \
    --if-none-match abcdef
```
{: pre}

### Example output
{: #power-hadr-cluster-node-delete-cli-output}

```
ID                       crn:v1:staging:public:power-dr-automation:us-south:a/123:123
Primary Node Details    -
Secondary Node Details   -

```
```
{: screen}

## Deployment
{: #power-hadr-deployment-cli}

Provide options to manage the PowerHA configuration on PowerVS through deployment and fetching existing deployment details.

```sh
ibmcloud power-hadr powerhasm deployment --help
```


### `ibmcloud power-hadr powerhasm deployment get`
{: #power-hadr-cli-deployment-get-command}

Retrieves the PowerHA deployment configuration, status, and associated metadata.

```sh
ibmcloud power-hadr powerhasm deployment get --instance-id INSTANCE-ID [--if-none-match IF-NONE-MATCH]
```


#### Command options
{: #power-hadr-deployment-get-cli-options}

`--instance-id` (string)
:   Unique identifier of the provisioned instance. Required.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9-]+$/`.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

### Example
{: #power-hadr-deployment-get-examples}

```sh
ibmcloud power-hadr powerhasm deployment get \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --if-none-match abcdef
```
{: pre}

### Example output
{: #power-hadr-deployment-get-cli-output}

```

Cloud Account ID                111233
Creation Time                   2026-04-08T09:42:07Z
Custom Network                  -
Plan ID                         6903b758-58c6-4217-8124-2029
Powerha Cluster Name            TestCluster
Primary Cluster Nodes Details
                                Agent Status   Powerha installation completed
                                Cores          0.5
                                IP Address     10.0.0.1
                                Memory         5
                                Pha Level      728SP4
                                Region         osa21
                                VM ID          f35327d7-4463-43dc-82ef-b63123
                                VM Name        TestVM1
                                VM Status      ACTIVE
                                Workspace ID   e03d1b8d-1cc1-4842-bf9e-90122288

Primary Region Name             Osaka 21
Primary Workspace               e03d1b8d-1cc1-4842-bf9e-90288
Primary Workspace Name          TestWorkspace
Provision End Time              0001-01-01 00:00:00 +0000 UTC
ID                              crn:123
Provision Start Time            2026-04-08 09:43:17.859158898 +0000 UTC
Provision Status                Active
Region ID                       osa21
Resource Group                  crn:v1:staging:public:resource-controller::a/2333::resource-group:1233
Secondary Cluster Nodes         -
Service Description             Service instance is in active state
Service ID                      1234
Service Name                    TestService1

```
{: screen}

### `ibmcloud power-hadr powerhasm deployment create`
{: #power-hadr-cli-deployment-create-command}

Create a new PowerHA deployment for a given location and PowerVS workspace. Refer deploying the PowerHA on Powervs /docs/dr-automation-powervs?topic=dr-automation-powervs-getting-started-with-ha-automation-for-power-virtual-server for more details.

```sh
ibmcloud power-hadr powerhasm deployment create --instance-id INSTANCE-ID --location-id LOCATION-ID --primary-workspace PRIMARY-WORKSPACE [--api-key API-KEY] [--cluster-type CLUSTER-TYPE] [--configure-type CONFIGURE-TYPE] [--primary-cluster-nodes PRIMARY-CLUSTER-NODES] [--standby-cluster-nodes STANDBY-CLUSTER-NODES] [--primary-location PRIMARY-LOCATION] [--secondary-location SECONDARY-LOCATION] [--secondary-workspace SECONDARY-WORKSPACE] [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH]
```


#### Command options
{: #power-hadr-deployment-create-cli-options}

`--instance-id` (string)
:   Unique identifier of the provisioned instance. Required.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9-]+$/`.

`--location-id` (string)
:   Identifier for the deployment location. Required.

    The maximum length is `16` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9._:-]+$/`.

`--primary-workspace` (string)
:   Primary workspace identifier. Required.

    The maximum length is `2048` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9._:-]+$/`.

`--api-key` (string)
:   The API key associated with the request.

    The maximum length is `2048` characters. The minimum length is `1` character. The value must match regular expression `/^[A-Za-z0-9._:-]+$/`.

`--cluster-type` (string)
:   Type of PowerHA cluster being deployed.

    The maximum length is `16` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9._:-]+$/`.

`--configure-type` (string)
:   Configuration type for the deployment.

    The maximum length is `16` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9._:-]+$/`.

`--primary-cluster-nodes` ([]string)
:   List of primary cluster node VM IDs.

    The list items must match regular expression `/^[a-zA-Z0-9._:-]+$/`. The maximum length is `50` items. The minimum length is `0` items.

`--standby-cluster-nodes` ([]string)
:   List of standby cluster node VM IDs.

    The list items must match regular expression `/^[a-zA-Z0-9._:-]+$/`. The maximum length is `50` items. The minimum length is `0` items.

`--primary-location` (string)
:   Location identifier for the primary cluster.

    The maximum length is `16` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9._:-]+$/`.

`--secondary-location` (string)
:   Location identifier for the secondary cluster.

    The maximum length is `16` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9._:-]+$/`.

`--secondary-workspace` (string)
:   Secondary workspace identifier.

    The maximum length is `2048` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9._:-]+$/`.

`--accept-language` (string)
:   The language requested for the return document.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

### Example
{: #power-hadr-deployment-create-examples}

```sh
ibmcloud power-hadr powerhasm deployment create \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --location-id loc-us-south-01 \
    --primary-workspace workspace-primary \
    --api-key 123635364646fghrtfhbfdhb \
    --cluster-type standard \
    --configure-type automatic \
    --primary-cluster-nodes ede4c36e-002c-48da-992e-6039d230c478,ede4c36e-002c-48da-992e-6039d230c478 \
    --standby-cluster-nodes 843a8e1f-05bb-4164-8c73-de39e016c2b4,843a8e1f-05bb-4164-8c73-de39e016c2b4 \
    --primary-location us-south \
    --secondary-location us-east \
    --secondary-workspace workspace-secondary \
    --accept-language en-US \
    --if-none-match abcdef
```
{: pre}

### Example output
{: #power-hadr-deployment-create-cli-output}

```
 
Custom Network                  -
Primary Cluster Nodes Details   -
ID                              crn:v1:staging:public:power-dr-automation:us-south:a/123:123::
Secondary Cluster Nodes         -
```

{: screen}

## Event
{: #power-hadr-event-cli}

Shows event that got generated during various PowerHA operations such as provision creation, PHA Deployment Creation and Updation along with their corresponding actions and descriptions.

```sh
ibmcloud power-hadr powerhasm event --help
```


### `ibmcloud power-hadr powerhasm event list`
{: #power-hadr-cli-event-list-command}

Get PowerHA automation events since a specific timestamp.

```sh
ibmcloud power-hadr powerhasm event list --instance-id INSTANCE-ID [--time TIME] [--from-time FROM-TIME] [--to-time TO-TIME] [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH]
```


#### Command options
{: #power-hadr-event-list-cli-options}

`--instance-id` (string)
:   Unique identifier of the provisioned instance. Required.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9-]+$/`.

`--time` (string)
:   (deprecated - use from_time) A time in either ISO 8601 or unix epoch format.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[0-9T:\\-Z]+$/`.

`--from-time` (string)
:   A from query time in either ISO 8601 or unix epoch format.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-\\:T]+$/`.

`--to-time` (string)
:   A to query time in either ISO 8601 or unix epoch format.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[0-9T:\\-Z]+$/`.

`--accept-language` (string)
:   The language requested for the return document.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

### Example
{: #power-hadr-event-list-examples}

```sh
ibmcloud power-hadr powerhasm event list \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --time 2025-06-19T23:59:59Z \
    --from-time 2025-06-19T00:00:00Z \
    --to-time 2025-06-19T23:59:59Z \
    --accept-language en-US \
    --if-none-match abcdef
```
{: pre}

### Example output
{: #power-hadr-event-list-cli-output}

```

Events
         Action         installation
         Event ID       337bad51-8191-4379-b732-4b3c062322068147-17756468232287129182
         Level          info
         Message        PowerHA installation for instance 'crn:123' on node ' TestVm-1' has completed.
         Message Data
                        Instanceid   crn:123
                        Nodename     TestVm-1

         Resource       Agent
         Time           2026-04-08T11:13:43.228Z
         Time Stamp     -
         User
                        Email     xxx@ibm.com
                        User ID   IBMid-123
```
{: screen}

### `ibmcloud power-hadr powerhasm event get`
{: #power-hadr-cli-event-get-command}

Get a single PowerHA automation event.

```sh
ibmcloud power-hadr powerhasm event get --instance-id INSTANCE-ID --event-id EVENT-ID [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH]
```


#### Command options
{: #power-hadr-event-get-cli-options}

`--instance-id` (string)
:   Unique identifier of the provisioned instance. Required.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9-]+$/`.

`--event-id` (string)
:   Event ID. Required.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9-]+$/`.

`--accept-language` (string)
:   The language requested for the return document.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

### Example
{: #power-hadr-event-get-examples}

```sh
ibmcloud power-hadr powerhasm event get \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --event-id 00116b2a-9326-4024-839e-fb5364b76898 \
    --accept-language en-US \
    --if-none-match abcdef
```
{: pre}

### Example output
{: #power-hadr-event-get-cli-output}

```

Action         create
Event ID       337bad51-8191-4379-b732-4b3c06068147-17756909
Level          info
Message        Service Instance '337bad51-8191-4379-b732-4b3c060909' has been created successfully.
Message Data
               Instanceid   37bad51-8191-4379-b732-4b3c06068147-17756909

Resource       ProvisionID
Time           2026-04-08T09:42:07.919Z
Time Stamp     -
User
               User ID   admin

```
{: screen}

## Agent
{: #power-hadr-agent-cli}

Provide options to download the powerHA agent file and track the download progress through the job ID. The downloaded agent file can then be used to install PowerHA on a Power Virtual Server instance.

```sh
ibmcloud power-hadr powerhasm agent --help
```
```
NAME:
  agent - Provide options to download the powerHA agent file and track the download progress through the job ID. The downloaded agent file can then be used to install PowerHA on a Power Virtual Server instance.

USAGE:
  ibmcloud power-hadr powerhasm agent [action]

COMMANDS:
  download          Downloads PowerHA Agent file.
  download-status   Get the Job status of the downloaded powerHA agent file.

GLOBAL OPTIONS:
  -h, --help    Show help
  -q, --quiet   Suppresses verbose messages.

Use "ibmcloud power-hadr powerhasm agent <command> --help" for more information about a command.
```

### `ibmcloud power-hadr powerhasm agent download-status`
{: #power-hadr-cli-agent-download-status-command}

Returns the current status of the job associated with a PowerHA agent file download. It indicates whether the download job is in running, completed, or failed, along with relevant metadata such as job ID, Job creation time and last updated time.

```sh
ibmcloud power-hadr powerhasm agent download-status --instance-id INSTANCE-ID --job-id JOB-ID [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH]
```


#### Command options
{: #power-hadr-agent-download-status-cli-options}

`--instance-id` (string)
:   Unique identifier of the provisioned instance. Required.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9-]+$/`.

`--job-id` (string)
:   Unique ID to track the pha agent file download. Required.

    The maximum length is `64` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9_-]+$/`.

`--accept-language` (string)
:   The language requested for the return document.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

#### Example
{: #power-hadr-agent-download-status-examples}

```sh
ibmcloud power-hadr powerhasm agent download-status \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --job-id 4235r23r5vdfdf-2323 \
    --accept-language en-US \
    --if-none-match abcdef
```
{: pre}

### Example output
{: #power-hadr-agent-download-status-cli-output}

```

Bytes Downloaded      590848
Creation At           2026-04-13T08:48:21.856Z
File Name             powerhaagent.rte
Job ID                f35327d7-4463-43dc-82ef-b63123
Last Updated At       2026-04-13T08:48:22.554Z
Service Instance ID   337bad51-8191-4379-b732-423333
Status                completed
Total Bytes           590848
VM ID                 f35327d7-4463-43dc-82ef-b2322
```
{: screen}

### `ibmcloud power-hadr powerhasm agent download`
{: #power-hadr-cli-agent-download-command}

Validates the pvm instance and then creates a job for the download process, downloads the PowerHA agent file from the Cloud Object Storage (COS) location, and updates the job progress in real time. Users can use the job ID to query the download status, including whether the job is running, completed, or failed.

```sh
ibmcloud power-hadr powerhasm agent download --instance-id INSTANCE-ID --vm-name VM-NAME [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH]
```


#### Command options
{: #power-hadr-agent-download-cli-options}

`--instance-id` (string)
:   Unique identifier of the provisioned instance. Required.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9-]+$/`.

`--vm-name` (string)
:   Power Virtual Machine Instance Name. Required.

    The maximum length is `63` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9_-]+$/`.

`--accept-language` (string)
:   The language requested for the return document.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

### Example
{: #power-hadr-agent-download-examples}

```sh
ibmcloud power-hadr powerhasm agent download \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --vm-name vm-sai-01 \
    --accept-language en-US \
    --if-none-match abcdef \
    --output-file tempdir/example-output.txt
```
{: pre}

### Example output
{: #power-hadr-powervs-agent-download-output}

```
Output written to powerha_agent.rte
```
{: screen}

## Powervs-workspaces
{: #power-hadr--powervs-workspaces-cli}

### `ibmcloud power-hadr powerhasm powervs-workspaces`
{: #power-hadr-cli-powervs-workspaces-command}

```
ibmcloud power-hadr phasm powervs-workspaces -help
NAME:
  powervs-workspaces - Retrieves list of powerVS workspaces related to the PowerHA service instance based on location.

USAGE:
  ibmcloud power-hadr powerhasm powervs-workspaces --instance-id INSTANCE-ID --location-id LOCATION-ID [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH]

EXAMPLE:
  ibmcloud power-hadr powerhasm powervs-workspaces \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --location-id us-south \
    --accept-language en-US \
    --if-none-match abcdef

OPTIONS:
      --accept-language string   The language requested for the return document. The maximum length is 50 characters. The
                                 minimum length is 1 character.
      --if-none-match string     ETag for conditional requests (optional). The maximum length is 50 characters. The minimum
                                 length is 1 character.
      --instance-id string       Required. Unique identifier of the provisioned instance. The maximum length is 50 characters.
                                 The minimum length is 1 character.
      --location-id string       Required. Location ID value. The maximum length is 20 characters. The minimum length is 5
                                 characters.

GLOBAL OPTIONS:
  -h, --help                Show help
  -j, --jmes-query string   Provide a JMESPath query to customize output.
      --output string       Choose an output format - can be 'json', 'yaml', 'tui', or 'table'. (default "table")
  -q, --quiet               Suppresses verbose messages.

```

Retrieves list of powerVS workspaces related to the PowerHA service instance based on location.

```sh
ibmcloud power-hadr powerhasm powervs-workspaces --instance-id INSTANCE-ID --location-id LOCATION-ID [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH]
```


#### Command options
{: #power-hadr-powervs-workspaces-cli-options}

`--instance-id` (string)
:   Unique identifier of the provisioned instance. Required.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9-]+$/`.

`--location-id` (string)
:   Location ID value. Required.

    The maximum length is `20` characters. The minimum length is `5` characters. The value must match regular expression `/^[a-z]{2}-[a-z]+(-[0-9]+)?$/`.

`--accept-language` (string)
:   The language requested for the return document.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

#### Example
{: #power-hadr-powervs-workspaces-examples}

```sh
ibmcloud power-hadr powerhasm powervs-workspaces \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --location-id us-south \
    --accept-language en-US \
    --if-none-match abcdef
```
{: pre}

### Example output
{: #power-hadr-powervs-workspaces-cli-output}

```

Workspaces
             ID     0fb44e20-9042-44d7-aec8-b745251ba9cb100
             Name   Test1_workspace

             ID     3ecdf4d9-542e-45f1-9317-eae3cbee031b088
             Name   Test2_workspace

```
{: screen}

## Locations
{: #power-hadr-locations-cli}

### `ibmcloud power-hadr powerhasm locations`
{: #power-hadr-cli-locations-command}

```
ibmcloud power-hadr phasm locations -help
NAME:
  locations - Retrieves the list of PowerVS locations where PowerHA service is supported.

USAGE:
  ibmcloud power-hadr powerhasm locations --instance-id INSTANCE-ID [--if-none-match IF-NONE-MATCH]

EXAMPLE:
  ibmcloud power-hadr powerhasm locations \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --if-none-match abcdef

OPTIONS:
      --if-none-match string   ETag for conditional requests (optional). The maximum length is 50 characters. The minimum
                               length is 1 character.
      --instance-id string     Required. Unique identifier of the provisioned instance. The maximum length is 50 characters.
                               The minimum length is 1 character.

GLOBAL OPTIONS:
  -h, --help                Show help
  -j, --jmes-query string   Provide a JMESPath query to customize output.
      --output string       Choose an output format - can be 'json', 'yaml', 'tui', or 'table'. (default "table")
  -q, --quiet               Suppresses verbose messages.
```

Retrieves the list of PowerVS locations where PowerHA service is supported.

```sh
ibmcloud power-hadr powerhasm locations --instance-id INSTANCE-ID [--if-none-match IF-NONE-MATCH]
```


#### Command options
{: #power-hadr-locations-cli-options}

`--instance-id` (string)
:   Unique identifier of the provisioned instance. Required.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9-]+$/`.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

### Example
{: #power-hadr-locations-examples}

```sh
ibmcloud power-hadr powerhasm locations \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --if-none-match abcdef
```
{: pre}

### Example output
{: #power-hadr-locations-cli-output}

```

Locations
            ID     wdc07
            Name   Washington DC 07

            ID     wdc06
            Name   Washington DC 06
```
{: screen}

## Last Operation
{: #power-hadr-last-operation-cli}

### `ibmcloud power-hadr powerhasm last-operation`
{: #power-hadr-cli-last-operation-command}

```
ibmcloud power-hadr phasm last-operation -help
NAME:
  last-operation - Retrieves the most recent operation performed on the PowerHA service instance.

USAGE:
  ibmcloud power-hadr powerhasm last-operation --instance-id INSTANCE-ID [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH]

EXAMPLE:
  ibmcloud power-hadr powerhasm last-operation \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --accept-language en-US \
    --if-none-match abcdef

OPTIONS:
      --accept-language string   The language requested for the return document. The maximum length is 50 characters. The
                                 minimum length is 1 character.
      --if-none-match string     ETag for conditional requests (optional). The maximum length is 50 characters. The minimum
                                 length is 1 character.
      --instance-id string       Required. Unique identifier of the provisioned instance. The maximum length is 50 characters.
                                 The minimum length is 1 character.

GLOBAL OPTIONS:
  -h, --help                Show help
  -j, --jmes-query string   Provide a JMESPath query to customize output.
      --output string       Choose an output format - can be 'json', 'yaml', 'tui', or 'table'. (default "table")
  -q, --quiet               Suppresses verbose messages.

```

Retrieves the most recent operation performed on the PowerHA service instance.

```sh
ibmcloud power-hadr powerhasm last-operation --instance-id INSTANCE-ID [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH]
```


#### Command options
{: #power-hadr-last-operation-cli-options}

`--instance-id` (string)
:   Unique identifier of the provisioned instance. Required.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9-]+$/`.

`--accept-language` (string)
:   The language requested for the return document.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

### Example
{: #power-hadr-last-operation-examples}

```sh
ibmcloud power-hadr powerhasm last-operation \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --accept-language en-US \
    --if-none-match abcdef
```
{: pre}

### Example output
{: #power-hadr-last-operation-cli-output}

```

Deployment Name   Test_PHA_Provision
Provision ID      crn:v1:staging:public:power-dr-automation:us-south:a/1244:123::
Resource Group    crn:v1:staging:public:resource-controller::a/123::resource-group:1223
Status            Active

```
{: screen}
