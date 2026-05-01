---
copyright:
  years: 2025
lastupdated: "2026-05-01"

subcollection: dr-automation-powervs

keywords: power-hadr, cli, pdr, commands

content-type: cli-docs

---


# DR Automation CLI commands
{: #dr-automation-cli-version}

## Available Commands:
{: #avalible-cmd}

`api-key` - Manage the API key for the DR Automation service instance.  
`deployment` - Manage disaster recovery deployment configuration and lifecycle operations.  
`event` - Retrieve events generated during DR Automation operations.  
`grs-location-pairs` - Retrieve GRS location pairs for the service instance.  
`locations` - Retrieve supported disaster recovery locations.  
`managed-vms` - Retrieve managed virtual machines for the service instance.  
`machine-types` - Retrieve supported machine types for deployment.  
`powervs-workspaces` - Retrieve PowerVS workspaces for DR deployment.  
`last-operation` - Retrieve the status of the last operation performed on the service instance.    

>**Note**: All the cli example outputs are shown below in `json` format.By default, cli output display in table format.To change the output format of cli, add `--output <format>` at  the end of command.

## Api Key
{: #power-hadr-api-key-cli}

Manage apikey.

```sh
ibmcloud power-hadr pdr api-key --help
```

```
NAME:
  api-key - Manage apikey.

USAGE:
  ibmcloud power-hadr pdr api-key [action]

COMMANDS:
  update   Updates the API key for the specified service instance.

GLOBAL OPTIONS:
  -h, --help    Show help
  -q, --quiet   Suppresses verbose messages.

Use "ibmcloud power-hadr pdr api-key <command> --help" for more information about a command.
```

### `ibmcloud power-hadr pdr api-key update`
{: #power-hadr-cli-api-key-update-command}

Updating the current API key details for the specified service instance.

```sh
ibmcloud power-hadr pdr api-key update --instance-id INSTANCE-ID --api-key API-KEY [--accept-language ACCEPT-LANGUAGE]
```


### Command options
{: #power-hadr-api-key-update-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

    The maximum length is `512` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_:\/.]+$/`.

`--api-key` (string)
:   The new API key value that will replace the existing one. Required.

    The maximum length is `256` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--accept-language` (string)
:   The language requested for the return document.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z\\-_,;=.*]+$/`.

### Example
{: #power-hadr-api-key-update-examples}

```sh
ibmcloud power-hadr pdr api-key update \
    --instance-id 123456d3-1122-3344-b67d-4389b44b7bf9 \
    --api-key adfadfdsafsdfdsf \
    --accept-language exampleString
```
{: pre}

### Example output
{: #power-hadr-api-key-update-cli-output}

```
Description   Key is valid.
Status        Key Updated Successfully
```
{: screen}

## Deployment
{: #power-hadr-deployment-cli}

Provide options to manage the DR configuration through deployment and fetching existing deployment details.

```sh
ibmcloud power-hadr pdr deployment --help
```

### `ibmcloud power-hadr pdr deployment get`
{: #power-hadr-cli-deployment-get-command}

```
NAME:
  deployment - Provide options to manage the DR configuration through deployment and fetching existing deployment details.

USAGE:
  ibmcloud power-hadr pdr deployment [action]

COMMANDS:
  create   Create DR Deployment.
  get      Disaster recovery deployment details.

GLOBAL OPTIONS:
  -h, --help    Show help
  -q, --quiet   Suppresses verbose messages.

Use "ibmcloud power-hadr pdr deployment <command> --help" for more information about a command.

```

Retrieves the disaster recovery (DR) summary details for the specified service instance, including key configuration, status information and managed vm details.

```sh
ibmcloud power-hadr pdr deployment get --instance-id INSTANCE-ID [--accept-language ACCEPT-LANGUAGE]
```


### Command options
{: #power-hadr-deployment-get-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

    The maximum length is `512` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_:\/.]+$/`.

`--accept-language` (string)
:   The language requested for the return document.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z\\-_,;=.*]+$/`.

### Example
{: #power-hadr-deployment-get-examples}

```sh
ibmcloud power-hadr pdr deployment get \
    --instance-id 123456d3-1122-3344-b67d-4389b44b7bf9 \
    --accept-language exampleString
```
{: pre}

### Example output
{: #power-hadr-deployment-get-cli-output}

```
Managed VM List        -
Orchestrator Details
                       Last Updated Orchestrator Deployment Time           2026-04-13T11:59:10.597Z
                       Last Updated Standby Orchestrator Deployment Time   0001-01-01T00:00:00.000Z
                       Latest Orchestrator Time                            2026-04-13T11:08:55.000Z
                       Location ID                                         syd04
                       Mfa Enabled                                         false
                       Orch Ext Connectivity Status                        Active
                       Orch Standby Node Addition Status
                       Orchestrator Cluster Message                        ksys is running fine
                       Orchestrator Config Status                          KSYS-DISCOVERY-SUCCESS
                       Orchestrator Group Leader
                       Orchestrator Location Type                          off-premises
                       Orchestrator Name                                   TestVM1
                       Orchestrator Status                                 ACTIVE
                       Orchestrator Workspace Name                         Test-workspace
                       Proxy IP
                       Schematic Workspace Name
                       Schematic Workspace Status
                       SSH Key Name                                        sshkeyname
                       Standby Orchestrator Name
                       Standby Orchestrator Status
                       Standby Orchestrator Workspace Name
                       Standby SSH Key Name
                       Transit Gateway Name
                       VPC Name

Service Details
                       CRN                                  crn:v1:staging:public:power-dr-automation:global:a/123:123::
                       Deployment Name                      TestCLI
                       Description                          5/5: Primary orchestrator Test-CLI is successfully deployed in 34m42s
                       Orchestrator Ha                      false
                       Plan Name                            DR Automation Public Plan
                       Primary IP Address                   10.0.47.197
                       Primary Orchestrator Dashboard URL   https://10.0.47.197:3000/login?byCloud=true
                       Recovery Location
                       Resource Group                       crn:v1:staging:public:resource-controller::a/123::resource-group:123
                       Standby Description
                       Standby IP Address
                       Standby Orchestrator Dashboard URL
                       Standby Status
                       Status                               ACTIVE

```
{: screen}

### `ibmcloud power-hadr pdr deployment create`
{: #power-hadr-cli-deployment-create-command}

Creates DR Deployment by creating Orchestrator instance in the given PowerVS workspace and configuration. Orchestrator instance can be used to manage multiple virtual servers and ensure continuous availability. For more details, refer Deploying the Orchestrator - /docs/dr-automation-powervs?topic=dr-automation-powervs-idep-the-orch.

```sh
ibmcloud power-hadr pdr deployment create --instance-id INSTANCE-ID --location-id LOCATION-ID --machine-type MACHINE-TYPE --orchestrator-location-type ORCHESTRATOR-LOCATION-TYPE --orchestrator-name ORCHESTRATOR-NAME --orchestrator-password ORCHESTRATOR-PASSWORD --orchestrator-workspace-id ORCHESTRATOR-WORKSPACE-ID [--api-key API-KEY] [--managed-apikey MANAGED-APIKEY] [--client-id CLIENT-ID] [--client-secret CLIENT-SECRET] [--guid GUID] [--orchestrator-ha=ORCHESTRATOR-HA] [--orchestrator-network-ids ORCHESTRATOR-NETWORK-IDS] [--orchestrator-workspace-location ORCHESTRATOR-WORKSPACE-LOCATION] [--proxy-ip PROXY-IP] [--region-id REGION-ID] [--resource-instance RESOURCE-INSTANCE] [--secondary-workspace-id SECONDARY-WORKSPACE-ID] [--secret SECRET] [--secret-group SECRET-GROUP] [--ssh-key-name SSH-KEY-NAME] [--standby-machine-type STANDBY-MACHINE-TYPE] [--standby-orchestrator-name STANDBY-ORCHESTRATOR-NAME] [--standby-orchestrator-network-ids STANDBY-ORCHESTRATOR-NETWORK-IDS] [--standby-ssh-key-name STANDBY-SSH-KEY-NAME] [--standby-orchestrator-workspace-id STANDBY-ORCHESTRATOR-WORKSPACE-ID] [--standby-orchestrator-workspace-location STANDBY-ORCHESTRATOR-WORKSPACE-LOCATION] [--standby-tier STANDBY-TIER] [--tenant-name TENANT-NAME] [--tier TIER] [--stand-by-redeploy STAND-BY-REDEPLOY] [--accept-language ACCEPT-LANGUAGE] [--accepts-incomplete=ACCEPTS-INCOMPLETE]
```


### Command options
{: #power-hadr-deployment-create-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

    The maximum length is `512` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_:\/.]+$/`.

`--location-id` (string)
:   The location or data center identifier where the service instance is deployed. Required.

    The maximum length is `32` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--machine-type` (string)
:   The machine type used for deploying orchestrator. Required.

    The maximum length is `32` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--orchestrator-location-type` (string)
:   The cloud location where your orchestator need to be created. Required.

    The maximum length is `32` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--orchestrator-name` (string)
:   The username used for the orchestrator. Required.

    The maximum length is `64` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--orchestrator-password` (string)
:   The password that you can use to access your orchestrator. Required.

    The maximum length is `256` characters. The minimum length is `1` character. The value must match regular expression `/^[\\x20-\\x7E]*$/`.

`--orchestrator-workspace-id` (string)
:   The unique identifier orchestrator workspace. Required.

    The maximum length is `64` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--api-key` (string)
:   The api Key of the service instance for deploying the disaster recovery service.

    The maximum length is `256` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--managed-apikey` (string)
:   APIKey used to manage the workloads by adding the PowerVS instances to the orchestrator.

    The maximum length is `256` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--client-id` (string)
:   The Client Id created for MFA authentication API.

    The maximum length is `64` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--client-secret` (string)
:   The client secret created for MFA authentication API.

    The maximum length is `256` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--guid` (string)
:   The global unique identifier of the service instance.

    The maximum length is `64` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--orchestrator-ha` (bool)
:   Indicates whether the orchestrator High Availability (HA) is enabled for the service instance.

`--orchestrator-network-ids` ([]string)
:   List of network IDs for primary orchestrator VM.

    The list items must match regular expression `/^[a-zA-Z0-9\\-_]+$/`. The maximum length is `10` items. The minimum length is `0` items.

`--orchestrator-workspace-location` (string)
:   The location of the orchestrator workspace.

    The maximum length is `32` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--proxy-ip` (string)
:   Proxy IP for the Communication between Orchestrator and Service broker.

    The maximum length is `64` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9.\\-_:]+$/`.

`--region-id` (string)
:   The power virtual server region where the service instance is deployed.

    The maximum length is `32` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--resource-instance` (string)
:   The uniquie identifier of the associated IBM Cloud resource instance.

    The maximum length is `512` characters. The minimum length is `1` character. The value must match regular expression `/^crn:v1:[a-zA-Z0-9\\-_]+:public:resource-controller:[a-zA-Z0-9\\-_]+:[a-zA-Z0-9\\-_\/]+:[a-zA-Z0-9\\-_]+::$/`.

`--secondary-workspace-id` (string)
:   The unique identifier of the secondary workspace used for the disaster recovery.

    The maximum length is `64` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--secret` (string)
:   The secret name or identifier used for retrieving credentials from secrets manager.

    The maximum length is `64` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--secret-group` (string)
:   The secret group name in IBM Cloud Secrets Manager containing sensitive data for the service instance.

    The maximum length is `64` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--ssh-key-name` (string)
:   The name of the SSH key used for deploying the orchestator.

    The maximum length is `64` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--standby-machine-type` (string)
:   The machine type used for deploying standby virtual machines.

    The maximum length is `32` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--standby-orchestrator-name` (string)
:   The username for the standby orchestrator management interface.

    The maximum length is `64` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--standby-orchestrator-network-ids` ([]string)
:   List of network IDs for standby orchestrator VM.

    The list items must match regular expression `/^[a-zA-Z0-9\\-_]+$/`. The maximum length is `10` items. The minimum length is `0` items.

`--standby-ssh-key-name` (string)
:   The name of the SSH key used for deploying the standby orchestator.

    The maximum length is `64` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--standby-orchestrator-workspace-id` (string)
:   The unique identifier of the standby orchestrator workspace.

    The maximum length is `64` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--standby-orchestrator-workspace-location` (string)
:   The location of the standby orchestrator workspace.

    The maximum length is `32` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--standby-tier` (string)
:   The storage tier used for deploying standby orchestrator.

    The maximum length is `32` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--tenant-name` (string)
:   The tenant name for MFA authentication API.

    The maximum length is `64` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9.\\-]+$/`.

`--tier` (string)
:   The storage tier used for deploying primary orchestrator.

    The maximum length is `32` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--stand-by-redeploy` (string)
:   Flag to indicate if standby should be redeployed (must be "true" or "false").

    The maximum length is `5` characters. The minimum length is `1` character. The value must match regular expression `/^(true|false)$/`.

`--accept-language` (string)
:   The language requested for the return document.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z\\-_,;=.*]+$/`.

`--accepts-incomplete` (bool)
:   A value of true indicates that both the IBM Cloud platform and the requesting client support asynchronous deprovisioning.

    The default value is `true`.

### Example
{: #power-hadr-deployment-create-examples}

```sh
ibmcloud power-hadr pdr deployment create \
    --instance-id 123456d3-1122-3344-b67d-4389b44b7bf9 \
    --location-id dal10 \
    --machine-type bx2-4x16 \
    --orchestrator-location-type off-premises \
    --orchestrator-name adminUser \
    --orchestrator-password exampleString \
    --orchestrator-workspace-id orch-workspace-01 \
    --api-key exampleString \
    --managed-apikey exampleString \
    --client-id abcd-97d2-1234-bf62-8eaecc67a1234 \
    --client-secret abcd1234xM1y123wK6qR9123456789bE2jG0pabcdefgh \
    --guid 123e4567-e89b-12d3-a456-426614174000 \
    --orchestrator-ha=true \
    --orchestrator-network-ids d9c7f1ab-47b2-4e6f-b0a8-9d2e5d7f5678,8ab29d71-8321-44d4-9cae-119fdc30a8ab \
    --orchestrator-workspace-location us-south \
    --proxy-ip 10.40.30.10:8888 \
    --region-id us-south \
    --resource-instance crn:v1:bluemix:public:resource-controller:us-south:a/123456fb04ceebfb4a9fd38c22334455:resource-instance:: \
    --secondary-workspace-id secondary-workspace789 \
    --secret exampleString \
    --secret-group default-secret-group \
    --ssh-key-name sshkey-name \
    --standby-machine-type bx2-8x32 \
    --standby-orchestrator-name standbyAdmin \
    --standby-orchestrator-network-ids d9c7f1ab-47b2-4e6f-b0a8-9d2e5d7f5678,8ab29d71-8321-44d4-9cae-119fdc30a8ab \
    --standby-ssh-key-name standby-sshkey-name \
    --standby-orchestrator-workspace-id orch-standby-02 \
    --standby-orchestrator-workspace-location us-east \
    --standby-tier Premium \
    --tenant-name xxx.ibm.com \
    --tier Standard \
    --stand-by-redeploy exampleString \
    --accept-language exampleString \
    --accepts-incomplete=true
```
{: pre}

### Example output
{: #power-hadr-deployment-create-cli-output}

```
  Dashboard Url  https://power-dra.cloud.ibm.com/power-dra-ui?instance_id=crn:v1:bluemix:public:power-dr-automation:us-south:a/123:123::",
  Id  crn:v1:staging:public:power-dr-automation:global:a/123:123::

```
{: screen}

## Event
{: #power-hadr-event-cli}

Shows event that got generated during various DR Automation operations such as provision creation, ManageDR Creation, image download, virtual server instance creation, orchestrator cluster creation, API Key updation along with their corresponding actions and descriptions.

```sh
ibmcloud power-hadr pdr event --help
```

```
NAME:
  event - Shows event that got generated during various DR Automation operations such as provision creation, ManageDR Creation, image download, virtual server instance creation, orchestrator cluster creation, API Key updation along with their corresponding actions and descriptions.

USAGE:
  ibmcloud power-hadr pdr event [action]

COMMANDS:
  get    Get a single event.
  list   Get events from the cloud instance since a specific timestamp.

GLOBAL OPTIONS:
  -h, --help    Show help
  -q, --quiet   Suppresses verbose messages.

Use "ibmcloud power-hadr pdr event <command> --help" for more information about a command.

```

### `ibmcloud power-hadr pdr event list`
{: #power-hadr-cli-event-list-command}

Retrieves the list of events from the specified service instance ID.

```sh
ibmcloud power-hadr pdr event list --instance-id INSTANCE-ID [--from-time FROM-TIME] [--to-time TO-TIME] [--accept-language ACCEPT-LANGUAGE]
```


### Command options
{: #power-hadr-event-list-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

    The maximum length is `512` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_:\/.]+$/`.

`--from-time` (string)
:   A from query time in either ISO 8601 or unix epoch format.

    The maximum length is `64` characters. The minimum length is `1` character. The value must match regular expression `/^(\\d{10}|\\d{13}|\\d{4}-\\d{2}-\\d{2}[T ]\\d{2}:\\d{2}:\\d{2}(\\.\\d+)?(Z|[+\\-]\\d{2}:\\d{2})?)$/`.

`--to-time` (string)
:   A to query time in either ISO 8601 or unix epoch format.

    The maximum length is `64` characters. The minimum length is `1` character. The value must match regular expression `/^(\\d{10}|\\d{13}|\\d{4}-\\d{2}-\\d{2}[T ]\\d{2}:\\d{2}:\\d{2}(\\.\\d+)?(Z|[+\\-]\\d{2}:\\d{2})?)$/`.

`--accept-language` (string)
:   The language requested for the return document.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z\\-_,;=.*]+$/`.

### Example
{: #power-hadr-event-list-examples}

```sh
ibmcloud power-hadr pdr event list \
    --instance-id 123456d3-1122-3344-b67d-4389b44b7bf9 \
    --from-time 2025-06-19T00:00:00Z \
    --to-time 2025-06-19T23:59:59Z \
    --accept-language exampleString
```
{: pre}

### Example output
{: #power-hadr-event-list-cli-output}

```
Events
         Action         update
         Event ID       e4c62998-b17a-4f52-b1e1-16283d619077-1776087630124372248
         Level          info
         Message        API key for service instance 'e4c62998-b17a-4f52-b1e1-16283d619077' has been updated successfully.
         Message Data
                        Instanceid   e4c62998-b17a-4f52-b1e1-16283d619077

         Resource       APIkey
         Time           2026-04-13T13:40:30.124Z
         Timestamp      1776087630
         User
                        Email     xxx1@ibm.com
                        User ID   IBMid-2020


         Action         update
         Event ID       e4c62998-b17a-4f52-b1e1-16283d619077-1776087579978693418
         Level          error
         Message        Failed to update API key for service instance 'e4c62998-b17a-4f52-b1e1-16283d619077', the provided API key is invalid.
         Message Data
                        Instanceid   e4c62998-b17a-4f52-b1e1-16283d619077

         Resource       APIkey
         Time           2026-04-13T13:39:39.978Z
         Timestamp      1776087579
         User
                        Email     xxx1@ibm.com
                        User ID   IBMid-2020


```
{: screen}

### `ibmcloud power-hadr pdr event get`
{: #power-hadr-cli-event-get-command}

Retrieves the details of a specific event for the given service instance provision ID.

```sh
ibmcloud power-hadr pdr event get --instance-id INSTANCE-ID --event-id EVENT-ID [--accept-language ACCEPT-LANGUAGE]
```


### Command options
{: #power-hadr-event-get-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

    The maximum length is `512` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_:\/.]+$/`.

`--event-id` (string)
:   Event ID. Required.

    The maximum length is `64` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--accept-language` (string)
:   The language requested for the return document.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z\\-_,;=.*]+$/`.

### Example
{: #power-hadr-event-get-examples}

```sh
ibmcloud power-hadr pdr event get \
    --instance-id 123456d3-1122-3344-b67d-4389b44b7bf9 \
    --event-id 00116b2a-9326-4024-839e-fb5364b76898 \
    --accept-language exampleString
```
{: pre}

### Example output
{: #power-hadr-event-get-cli-output}

```
Action         create
Event ID       e4c62998-b17a-4f52-b1e1-16283d619077-1776079343268534848
Level          info
Message        Service Instance 'e4c62998-b17a-4f52-b1e1-16283d619077' has been created successfully.
Message Data
               Instanceid   e4c62998-b17a-4f52-b1e1-16283d619077

Resource       ProvisionID
Time           2026-04-13T11:22:23.268Z
Timestamp      1776079343
User
               User ID   admin

```
{: screen}

## GRS Location Pairs
{: #power-hadr-grs-location-pairs-cli}

### `ibmcloud power-hadr pdr grs-location-pairs`
{: #power-hadr-cli-grs-location-pairs-command}

```
ibmcloud power-hadr pdr grs-location-pairs --help
```
```
NAME:
  grs-location-pairs - Retrieves the (GRS) location pairs associated with the specified service instance based on managed VMs.

USAGE:
  ibmcloud power-hadr pdr grs-location-pairs --instance-id INSTANCE-ID [--accept-language ACCEPT-LANGUAGE]

EXAMPLE:
  ibmcloud power-hadr pdr grs-location-pairs \
    --instance-id 123456d3-1122-3344-b67d-4389b44b7bf9 \
    --accept-language exampleString

OPTIONS:
      --accept-language string   The language requested for the return document. The maximum length is 50 characters. The
                                 minimum length is 1 character.
      --instance-id string       Required. instance id of instance to provision. The maximum length is 512 characters. The
                                 minimum length is 1 character.

GLOBAL OPTIONS:
  -h, --help                Show help
  -j, --jmes-query string   Provide a JMESPath query to customize output.
      --output string       Choose an output format - can be 'json', 'yaml', 'tui', or 'table'. (default "table")
  -q, --quiet               Suppresses verbose messages.

```
Retrieves the (GRS) location pairs associated with the specified service instance based on managed VMs.

```sh
ibmcloud power-hadr pdr grs-location-pairs --instance-id INSTANCE-ID [--accept-language ACCEPT-LANGUAGE]
```


### Command options
{: #power-hadr-grs-location-pairs-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

    The maximum length is `512` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_:\/.]+$/`.

`--accept-language` (string)
:   The language requested for the return document.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z\\-_,;=.*]+$/`.

### Example
{: #power-hadr-grs-location-pairs-examples}

```sh
ibmcloud power-hadr pdr grs-location-pairs \
    --instance-id 123456d3-1122-3344-b67d-4389b44b7bf9 \
    --accept-language exampleString
```


{: pre}

### Example output
{: #power-hadr-grs-location-pairs-cli-output}

```
Location Pairs
                 Syd04   syd05

```
{: screen}

## Locations
{: #power-hadr-dr-locations-cli}

### `ibmcloud power-hadr pdr locations`
{: #power-hadr-cli-locations-command}

```
ibmcloud power-hadr pdr locations --help
```
```
NAME:
  locations - Retrieves the list of disaster recovery (DR) locations available for the specified service instance.

USAGE:
  ibmcloud power-hadr pdr locations --instance-id INSTANCE-ID [--accept-language ACCEPT-LANGUAGE]

EXAMPLE:
  ibmcloud power-hadr pdr locations \
    --instance-id 123456d3-1122-3344-b67d-4389b44b7bf9 \
    --accept-language exampleString

OPTIONS:
      --accept-language string   The language requested for the return document. The maximum length is 50 characters. The
                                 minimum length is 1 character.
      --instance-id string       Required. instance id of instance to provision. The maximum length is 512 characters. The
                                 minimum length is 1 character.

GLOBAL OPTIONS:
  -h, --help                Show help
  -j, --jmes-query string   Provide a JMESPath query to customize output.
      --output string       Choose an output format - can be 'json', 'yaml', 'tui', or 'table'. (default "table")
  -q, --quiet               Suppresses verbose messages.
```

Retrieves the list of disaster recovery (DR) locations available for the specified service instance.

```sh
ibmcloud power-hadr pdr locations --instance-id INSTANCE-ID [--accept-language ACCEPT-LANGUAGE]
```


### Command options
{: #power-hadr-locations-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

    The maximum length is `512` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_:\/.]+$/`.

`--accept-language` (string)
:   The language requested for the return document.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z\\-_,;=.*]+$/`.

### Example
{: #power-hadr-locations-examples}

```sh
ibmcloud power-hadr pdr locations \
    --instance-id 123456d3-1122-3344-b67d-4389b44b7bf9 \
    --accept-language exampleString
```
{: pre}

### Example output
{: #power-hadr-locations-cli-output}

```
Dr Locations
               ID     wdc07
               Name   Washington DC 07

               ID     wdc06
               Name   Washington DC 06

               ID     us-south
               Name   Dallas 13
```
{: screen}

## Managed Vms
{: #power-hadr-managed-vms-cli}

### `ibmcloud power-hadr pdr managed-vms`
{: #power-hadr-cli-managed-vms-command}

```
ibmcloud power-hadr pdr managed-vms --help
```
```
NAME:
  managed-vms - Retrieves the list of disaster recovery (DR) managed virtual machines for the specified service instance.

USAGE:
  ibmcloud power-hadr pdr managed-vms --instance-id INSTANCE-ID [--accept-language ACCEPT-LANGUAGE]

EXAMPLE:
  ibmcloud power-hadr pdr managed-vms \
    --instance-id 123456d3-1122-3344-b67d-4389b44b7bf9 \
    --accept-language exampleString

OPTIONS:
      --accept-language string   The language requested for the return document. The maximum length is 50 characters. The
                                 minimum length is 1 character.
      --instance-id string       Required. instance id of instance to provision. The maximum length is 512 characters. The
                                 minimum length is 1 character.

GLOBAL OPTIONS:
  -h, --help                Show help
  -j, --jmes-query string   Provide a JMESPath query to customize output.
      --output string       Choose an output format - can be 'json', 'yaml', 'tui', or 'table'. (default "table")
  -q, --quiet               Suppresses verbose messages.
```

Retrieves the list of disaster recovery (DR) managed virtual machines for the specified service instance.

```sh
ibmcloud power-hadr pdr managed-vms --instance-id INSTANCE-ID [--accept-language ACCEPT-LANGUAGE]
```


### Command options
{: #power-hadr-managed-vms-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

    The maximum length is `512` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_:\/.]+$/`.

`--accept-language` (string)
:   The language requested for the return document.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z\\-_,;=.*]+$/`.

### Example
{: #power-hadr-managed-vms-examples}

```sh
ibmcloud power-hadr pdr managed-vms \
    --instance-id 123456d3-1122-3344-b67d-4389b44b7bf9 \
    --accept-language exampleString
```
{: pre}

### Example output
{: #power-hadr-managed-vms-cli-output}

```
Managed VM List
                  D5b858d1-cf0e-431d-8934-b78443cfc473
                                                         Core              0.25
                                                         Dr Average Time   -1
                                                         Dr Region         syd05
                                                         Memory            2
                                                         Region            syd04
                                                         VM Name           TestVm1
                                                         Workgroup Name    TestVm1-wd02
                                                         Workspace Name    Test-workspace
```
{: screen}

## Machine Types
{: #power-hadr-dr-automation-ibm-cloud-cli}

### `ibmcloud power-hadr pdr machine-types`
{: #power-hadr-cli-machine-types-command}

```
ibmcloud power-hadr pdr machine-types --help
```
```
NAME:
  machine-types - Retrieves the list of supported machine types for the given workspace. This endpoint is used to identify machine types available for disaster recovery automation.

USAGE:
  ibmcloud power-hadr pdr machine-types --instance-id INSTANCE-ID --primary-workspace-name PRIMARY-WORKSPACE-NAME [--accept-language ACCEPT-LANGUAGE] [--standby-workspace-name STANDBY-WORKSPACE-NAME]

EXAMPLE:
  ibmcloud power-hadr pdr machine-types \
    --instance-id 123456d3-1122-3344-b67d-4389b44b7bf9 \
    --primary-workspace-name Test-workspace-wdc06 \
    --accept-language exampleString \
    --standby-workspace-name Test-workspace-wdc07

OPTIONS:
      --accept-language string          The language requested for the return document. The maximum length is 50 characters.
                                        The minimum length is 1 character.
      --instance-id string              Required. instance id of instance to provision. The maximum length is 512 characters.
                                        The minimum length is 1 character.
      --primary-workspace-name string   Required. The primary Power virtual server workspace name. The maximum length is 64
                                        characters. The minimum length is 1 character.
      --standby-workspace-name string   The standby Power virtual server workspace name. The maximum length is 64 characters.
                                        The minimum length is 1 character.

GLOBAL OPTIONS:
  -h, --help                Show help
  -j, --jmes-query string   Provide a JMESPath query to customize output.
      --output string       Choose an output format - can be 'json', 'yaml', 'tui', or 'table'. (default "table")
  -q, --quiet               Suppresses verbose messages.
```

Retrieves the list of supported machine types for the given workspace. This endpoint is used to identify machine types available for disaster recovery automation.

```sh
ibmcloud power-hadr pdr machine-types --instance-id INSTANCE-ID --primary-workspace-name PRIMARY-WORKSPACE-NAME [--accept-language ACCEPT-LANGUAGE] [--standby-workspace-name STANDBY-WORKSPACE-NAME]
```


### Command options
{: #power-hadr-machine-types-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

    The maximum length is `512` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_:\/.]+$/`.

`--primary-workspace-name` (string)
:   The primary Power virtual server workspace name. Required.

    The maximum length is `64` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

`--accept-language` (string)
:   The language requested for the return document.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z\\-_,;=.*]+$/`.

`--standby-workspace-name` (string)
:   The standby Power virtual server workspace name.

    The maximum length is `64` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

### Example
{: #power-hadr-machine-types-examples}

```sh
ibmcloud power-hadr pdr machine-types \
    --instance-id 123456d3-1122-3344-b67d-4389b44b7bf9 \
    --primary-workspace-name Test-workspace-wdc06 \
    --accept-language exampleString \
    --standby-workspace-name Test-workspace-wdc07
```
{: pre}

```
Workspaces
             Test-workspace-syd04   s922, e980, s1022

```
{: screen}

## Powervs Workspaces
{: #power-hadr-cli-powervs-workspace-command}

### `ibmcloud power-hadr pdr powervs-workspaces`
{: #power-hadr-cli-powervs-workspaces-command}

```
ibmcloud power-hadr pdr powervs-workspaces --help
```
```
NAME:
  powervs-workspaces - Retrieves the power virtual server workspaces for primary and standby orchestrator based on location id.

USAGE:
  ibmcloud power-hadr pdr powervs-workspaces --instance-id INSTANCE-ID --location-id LOCATION-ID

EXAMPLE:
  ibmcloud power-hadr pdr powervs-workspaces \
    --instance-id 123456d3-1122-3344-b67d-4389b44b7bf9 \
    --location-id exampleString

OPTIONS:
      --instance-id string   Required. instance id of instance to provision. The maximum length is 512 characters. The minimum
                             length is 1 character.
      --location-id string   Required. Location ID value. The maximum length is 32 characters. The minimum length is 1 character.

GLOBAL OPTIONS:
  -h, --help                Show help
  -j, --jmes-query string   Provide a JMESPath query to customize output.
      --output string       Choose an output format - can be 'json', 'yaml', 'tui', or 'table'. (default "table")
  -q, --quiet               Suppresses verbose messages.
```

Retrieves the Power Virtual Server workspaces associated with the primary and standby orchestrators for the given instance ID and location ID.

```sh
ibmcloud power-hadr pdr powervs-workspaces --instance-id INSTANCE-ID --location-id LOCATION-ID
```


### Command options
{: #power-hadr-powervs-workspaces-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

    The maximum length is `512` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_:\/.]+$/`.

`--location-id` (string)
:   Location ID value. Required.

    The maximum length is `32` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_]+$/`.

### Example
{: #power-hadr-powervs-workspaces-examples}

```sh
ibmcloud power-hadr pdr powervs-workspaces \
    --instance-id 123456d3-1122-3344-b67d-4389b44b7bf9 \
    --location-id exampleString
```
{: pre}

### Example output
{: #power-hadr-powervs-workspaces-cli-output}

``
Dr Standby Workspaces
                        Details
                                   CRN   crn:v1:bluemix:public:power-iaas:che01:a/094f4214c75941f991da601b001df1fe:0afdb5d1-1a1d-4f9b-bc39-45913ce173be90::

                        ID         0afdb5d1-1a1d-4f9b-bc39-45913ce173be90
                        Location
                                   Region   che01
                                   Type     data-center
                                   URL      https://che.power-iaas.cloud.ibm.com

                        Name       Test1
                        Status     active

Dr Workspaces
                        Details
                                   CRN   crn:v1:bluemix:public:power-iaas:us-south:a/094f4214c75941f991da601b001df1fe:0fb44e20-9042-44d7-aec8-b745251ba9cb90::

                        ID         0fb44e20-9042-44d7-aec8-b745251ba9cb90
                        Location
                                   Region   us-south
                                   Type     region
                                   URL      https://us-south.power-iaas.cloud.ibm.com

                        Name       Test2
                        Status     active
```
```

## Last Operation
{: #power-hadr-last-operation-cli}

### `ibmcloud power-hadr pdr last-operation`
{: #power-hadr-cli-last-operation-command}

```
ibmcloud power-hadr pdr last-operation --help
```

```
NAME:
  last-operation - Retrieves the status of the last operation performed on the specified service instance, such as provisioning, updating, or deprovisioning.

USAGE:
  ibmcloud power-hadr pdr last-operation --instance-id INSTANCE-ID [--accept-language ACCEPT-LANGUAGE]

EXAMPLE:
  ibmcloud power-hadr pdr last-operation \
    --instance-id 123456d3-1122-3344-b67d-4389b44b7bf9 \
    --accept-language exampleString

OPTIONS:
      --accept-language string   The language requested for the return document. The maximum length is 50 characters. The
                                 minimum length is 1 character.
      --instance-id string       Required. instance id of instance to provision. The maximum length is 512 characters. The
                                 minimum length is 1 character.

GLOBAL OPTIONS:
  -h, --help                Show help
  -j, --jmes-query string   Provide a JMESPath query to customize output.
      --output string       Choose an output format - can be 'json', 'yaml', 'tui', or 'table'. (default "table")
  -q, --quiet               Suppresses verbose messages.
```
Retrieves the status of the last operation performed on the specified service instance, such as provisioning, updating, or deprovisioning.

```sh
ibmcloud power-hadr pdr last-operation --instance-id INSTANCE-ID [--accept-language ACCEPT-LANGUAGE]
```


### Command options
{: #power-hadr-last-operation-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

    The maximum length is `512` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_:\/.]+$/`.

`--accept-language` (string)
:   The language requested for the return document.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z\\-_,;=.*]+$/`.

### Example
{: #power-hadr-last-operation-examples}

```sh
ibmcloud power-hadr pdr last-operation \
    --instance-id 123456d3-1122-3344-b67d-4389b44b7bf9 \
    --accept-language exampleString
```
{: pre}

### Example output
{: #power-hadr-last-operation-cli-output}

```
CRN                                                 crn:v1:staging:public:power-dr-automation:global:a/123-123::
Deployment Name                                     TestCLI
Last Updated Orchestrator Deployment Time           2026-04-13T11:59:10.597Z
Last Updated Standby Orchestrator Deployment Time   0001-01-01T00:00:00.000Z
Mfa Enabled                                         false
Orch Ext Connectivity Status                        Active
Orch Standby Node Addtion Status                    -
Orchestrator Cluster Message                        ksys is running fine
Orchestrator Config Status                          KSYS-DISCOVERY-SUCCESS
Orchestrator Ha                                     false
Plan Name                                           DR Automation Public Plan
Primary Description                                 5/5: Primary orchestrator Test-CLI is successfully deployed in 34m42s
Primary Error Description
Primary IP Address                                  10.0.47.197
Primary Orchestrator Status                         ACTIVE
Recovery Location
Resource Group                                      crn:v1:staging:public:resource-controller::a/123::resource-group:123
Standby Description
Standby Error Description
Standby IP Address
Standby Status
Status                                              Active
Is API Key Expired                                  false
```
{: screen}
