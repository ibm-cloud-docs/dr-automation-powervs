---
copyright:
  years: 2026
lastupdated: "2026-03-25"

keywords: powerhaautomation service, cli, plugin

---

# PowerHA AIX CLI commands
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

#### Example output
{: #power-hadr-api-key-update-cli-output}

```json
{
  "description" : "API key created successfully",
  "example" : "adfadfdsafsdfdsf",
  "id" : "12345",
  "status" : "Success"
}
```
{: screen}

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


#### Command options
{: #power-hadr-cluster-node-get-cli-options}

`--instance-id` (string)
:   Unique identifier of the provisioned instance. Required.

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9-]+$/`.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

    The maximum length is `50` characters. The minimum length is `1` character. The value must match regular expression `/^[a-zA-Z0-9\\-_,;=.*]+$/`.

#### Example
{: #power-hadr-cluster-node-get-examples}

```sh
ibmcloud power-hadr powerhasm cluster-node get \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --if-none-match abcdef
```
{: pre}

#### Example output
{: #power-hadr-cluster-node-get-cli-output}

```json
{
  "id" : "123498690689",
  "primary_node_details" : [ {
    "cores" : 0,
    "ip_addresses" : [ "10.0.0.11", "192.168.1.11" ],
    "memory" : 16,
    "region" : "us-south",
    "vm_id" : "vm-primary-001",
    "vm_name" : "primary-node-1",
    "vm_status" : "active",
    "workspace_id" : "workspace-primary-001",
    "agent_status" : "running"
  } ],
  "secondary_node_details" : [ {
    "cores" : 0,
    "ip_addresses" : [ "10.1.0.11" ],
    "memory" : 16,
    "region" : "us-east",
    "vm_id" : "vm-secondary-001",
    "vm_name" : "secondary-node-1",
    "vm_status" : "standby",
    "workspace_id" : "workspace-secondary-001",
    "agent_status" : "running"
  } ]
}
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

#### Example
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

#### Example output
{: #power-hadr-cluster-node-add-cli-output}

```json
{
  "id" : "cluster-node-001",
  "primary_node_details" : [ {
    "cores" : 0,
    "ip_addresses" : [ "10.0.0.11", "192.168.1.11" ],
    "memory" : 16,
    "region" : "us-south",
    "vm_id" : "vm-primary-001",
    "vm_name" : "primary-node-1",
    "vm_status" : "active",
    "workspace_id" : "workspace-primary-001",
    "agent_status" : "running"
  } ],
  "secondary_node_details" : [ {
    "cores" : 0,
    "ip_addresses" : [ "10.1.0.11" ],
    "memory" : 16,
    "region" : "us-east",
    "vm_id" : "vm-secondary-001",
    "vm_name" : "secondary-node-1",
    "vm_status" : "standby",
    "workspace_id" : "workspace-secondary-001",
    "agent_status" : "running"
  } ]
}
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

#### Example output
{: #power-hadr-cluster-node-delete-cli-output}

```json
{
  "id" : "123498690689",
  "primary_node_details" : [ {
    "cores" : 0,
    "ip_addresses" : [ "10.0.0.11", "192.168.1.11" ],
    "memory" : 16,
    "region" : "us-south",
    "vm_id" : "vm-primary-001",
    "vm_name" : "primary-node-1",
    "vm_status" : "active",
    "workspace_id" : "workspace-primary-001",
    "agent_status" : "running"
  } ],
  "secondary_node_details" : [ {
    "cores" : 0,
    "ip_addresses" : [ "10.1.0.11" ],
    "memory" : 16,
    "region" : "us-east",
    "vm_id" : "vm-secondary-001",
    "vm_name" : "secondary-node-1",
    "vm_status" : "standby",
    "workspace_id" : "workspace-secondary-001",
    "agent_status" : "running"
  } ]
}
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

#### Example
{: #power-hadr-deployment-get-examples}

```sh
ibmcloud power-hadr powerhasm deployment get \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --if-none-match abcdef
```
{: pre}

#### Example output
{: #power-hadr-deployment-get-cli-output}

```json
{
  "cloud_account_id" : "cloud-acc-0001",
  "connectivity_type" : "vpc",
  "creation_time" : "2024-10-20T14:55:00Z",
  "custom_network" : [ "10.0.0.0/24", "10.0.1.0/24" ],
  "deprovision_time" : "2025-06-23T07:15:00Z",
  "guid" : "123e4567-e89b-12d3-a456-426614174000",
  "is_duplicate" : false,
  "plan_id" : "plan-456",
  "plan_name" : "standard-plan",
  "powerha_cluster_name" : "pha-cluster-prod",
  "powerha_cluster_type" : "standard",
  "powerha_level" : "7.2.4",
  "primary_cluster_nodes_details" : [ {
    "agent_status" : "active",
    "cores" : 8,
    "ip_address" : "10.0.0.11",
    "memory" : 16,
    "region" : "us-south",
    "vm_id" : "vm-primary-002",
    "vm_name" : "primary-node-2",
    "vm_status" : "running",
    "workspace_id" : "ws-primary-123"
  } ],
  "primary_location" : "DAL10",
  "primary_workspace" : "us-south",
  "provision_end_time" : "2024-10-21T09:10:12Z",
  "id" : "prov-987654321",
  "provision_start_time" : "2024-10-21T08:23:45Z",
  "provision_status" : "completed",
  "region_id" : "us-south",
  "resource_group" : "prod-rg",
  "resource_group_crn" : "crn:v1:staging:public:resource-group:global:a/123456::",
  "resource_instance" : "pha-instance-001",
  "secondary_cluster_nodes" : [ {
    "agent_status" : "active",
    "cores" : 8,
    "ip_address" : "10.0.1.10",
    "memory" : 16,
    "region" : "us-east",
    "vm_id" : "vm-secondary-001",
    "vm_name" : "secondary-node-1",
    "vm_status" : "running",
    "workspace_id" : "ws-secondary-999"
  } ],
  "secondary_location" : "WDC06",
  "secondary_workspace" : "us-east",
  "service_description" : "Primary DR Automation Service",
  "service_id" : "service-123",
  "service_name" : "powerha",
  "user_tags" : "env:prod,team:ha"
}
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

#### Example
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

#### Example output
{: #power-hadr-deployment-create-cli-output}

```json
{
  "cloud_account_id" : "cloud-acc-0001",
  "connectivity_type" : "vpc",
  "creation_time" : "2024-10-20T14:55:00Z",
  "custom_network" : [ "10.0.0.0/24", "10.0.1.0/24" ],
  "deprovision_time" : "2099-12-31T23:59:59Z",
  "guid" : "123e4567-e89b-12d3-a456-426614174000",
  "is_duplicate" : false,
  "plan_id" : "plan-456",
  "plan_name" : "standard-plan",
  "powerha_cluster_name" : "pha-cluster-prod",
  "powerha_cluster_type" : "standard",
  "powerha_level" : "7.2.4",
  "primary_cluster_nodes_details" : [ {
    "agent_status" : "active",
    "cores" : 8,
    "ip_address" : "10.0.0.11",
    "memory" : 16,
    "region" : "us-south",
    "vm_id" : "vm-primary-002",
    "vm_name" : "primary-node-2",
    "vm_status" : "running",
    "workspace_id" : "ws-primary-123"
  } ],
  "primary_location" : "DAL10",
  "primary_workspace" : "us-south",
  "provision_end_time" : "2024-10-21T09:10:12Z",
  "provision_id" : "prov-987654321",
  "provision_start_time" : "2024-10-21T08:23:45Z",
  "provision_status" : "completed",
  "region_id" : "us-south",
  "resource_group" : "prod-rg",
  "resource_group_crn" : "crn:v1:staging:public:resource-group:global:a/123456::",
  "resource_instance" : "pha-instance-001",
  "secondary_cluster_nodes" : [ {
    "agent_status" : "active",
    "cores" : 8,
    "ip_address" : "10.0.1.10",
    "memory" : 16,
    "region" : "us-east",
    "vm_id" : "vm-secondary-001",
    "vm_name" : "secondary-node-1",
    "vm_status" : "running",
    "workspace_id" : "ws-secondary-999"
  } ],
  "secondary_location" : "WDC06",
  "secondary_workspace" : "us-east",
  "service_description" : "Primary DR Automation Service",
  "service_id" : "service-123",
  "service_name" : "powerha",
  "user_tags" : "env:prod,team:ha"
}
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

#### Example
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

#### Example output
{: #power-hadr-event-list-cli-output}

```json
{
  "events" : [ {
    "action" : "create",
    "event_id" : "1cecfe43-43cd-4b1b-86be-30c2d3d2a25f",
    "level" : "info",
    "message" : "Service Instance 7222c899-a31a-4a0c-be03-75920d23cd16 has been created successfully",
    "minLength" : 1,
    "maxLength" : 128,
    "pattern" : "^[A-Za-z0-9 .,_:!?'"-]+$",
    "message_Data" : {
      "InstanceID" : {
        "id" : "7222c899-a31a-4a0c-be03-75920d23cd16"
      }
    },
    "metadata" : { },
    "resource" : "ProvisionID",
    "time" : "2025-06-23T07:12:49.840Z",
    "time_stamp" : "2025-06-23T07:12:49Z",
    "user" : {
      "user_id" : "admin"
    }
  }, {
    "action" : "create",
    "event_id" : "c49f0ced-2a78-48a6-929c-6b824555ddc6",
    "level" : "info",
    "message" : "Service Instance 7222c899-a31a-4a0c-be03-75920d23cd16 has been created successfully",
    "minLength" : 1,
    "maxLength" : 128,
    "pattern" : "^[A-Za-z0-9 .,_:!?'"-]+$",
    "message_Data" : {
      "InstanceID" : {
        "id" : "7222c899-a31a-4a0c-be03-75920d23cd16"
      }
    },
    "metadata" : { },
    "resource" : "managedr",
    "time" : "2025-06-23T07:14:53.871Z",
    "time_stamp" : "2025-06-23T07:12:49Z",
    "user" : {
      "email" : "abcuser@ibm.com",
      "user_id" : "IBMid-695000ab7E"
    }
  } ]
}
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

#### Example
{: #power-hadr-event-get-examples}

```sh
ibmcloud power-hadr powerhasm event get \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --event-id 00116b2a-9326-4024-839e-fb5364b76898 \
    --accept-language en-US \
    --if-none-match abcdef
```
{: pre}

#### Example output
{: #power-hadr-event-get-cli-output}

```json
{
  "action" : "create",
  "api_source" : "pha-automation-api",
  "event_id" : "1cecfe43-43cd-4b1b-86be-30c2d3d2a25f",
  "level" : "info",
  "message" : "Service Instance created successfully",
  "message_Data" : {
    "InstanceID" : {
      "id" : "7222c899-a31a-4a0c-be03-75920d23cd16"
    },
    "request_id" : {
      "id" : "req-12345"
    }
  },
  "metadata" : { },
  "resource" : "ProvisionID",
  "time" : "2025-06-23T07:12:49.840Z",
  "time_stamp" : "2025-06-23T07:12:49Z",
  "user" : {
    "user_email" : "example.user@ibm.com",
    "user_id" : "IBMid-123456"
  }
}
```
{: screen}

## Agent
{: #power-hadr-agent-cli}

Provide options to download the powerHA agent file and track the download progress through the job ID. The downloaded agent file can then be used to install PowerHA on a Power Virtual Server instance.

```sh
ibmcloud power-hadr powerhasm agent --help
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

#### Example output
{: #power-hadr-agent-download-status-cli-output}

```json
{
  "bytes_downloaded" : 1024,
  "creation_at" : "2025-01-12T10:00:00Z",
  "job_id" : "job-12345",
  "last_updated_at" : "2025-01-12T10:45:30Z",
  "service_instance_id" : "service-instance-12345",
  "status" : "running",
  "total_bytes" : 1024,
  "vm_id" : "vm-abcd1234"
}
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

#### Example
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

## Powerha Automation Config
{: #power-hadr-powerha-automation-config-cli}

### `ibmcloud power-hadr powerhasm powervs-workspaces`
{: #power-hadr-cli-powervs-workspaces-command}

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

#### Example output
{: #power-hadr-powervs-workspaces-cli-output}

```json
{
  "workspaces" : [ {
    "id" : "ws-001",
    "name" : "Primary-Workspace"
  }, {
    "id" : "ws-002",
    "name" : "Secondary-Workspace"
  } ]
}
```
{: screen}

## Powerha Automation Ibm Cloud
{: #power-hadr-powerha-automation-ibm-cloud-cli}

### `ibmcloud power-hadr powerhasm locations`
{: #power-hadr-cli-locations-command}

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

#### Example
{: #power-hadr-locations-examples}

```sh
ibmcloud power-hadr powerhasm locations \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --if-none-match abcdef
```
{: pre}

#### Example output
{: #power-hadr-locations-cli-output}

```json
{
  "locations" : [ {
    "id" : "loc-001",
    "name" : "us-south"
  }, {
    "id" : "loc-002",
    "name" : "eu-de"
  } ]
}
```
{: screen}

## Powerha Automation Service Instance
{: #power-hadr-powerha-automation-service-instance-cli}

### `ibmcloud power-hadr powerhasm last-operation`
{: #power-hadr-cli-last-operation-command}

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

#### Example
{: #power-hadr-last-operation-examples}

```sh
ibmcloud power-hadr powerhasm last-operation \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --accept-language en-US \
    --if-none-match abcdef
```
{: pre}

#### Example output
{: #power-hadr-last-operation-cli-output}

```json
{
  "deployment_name" : "pha-deployment-123",
  "provision_id" : "prov-987654321",
  "resource_group" : "prod-rg",
  "status" : "in-progress"
}
```
{: screen}
