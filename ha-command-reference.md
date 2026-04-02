---
copyright:
  years: 2026
lastupdated: "2026-03-25"

keywords: powerhaautomation service, cli, plugin

---

# {{site.data.keyword.DR_full}} PowerHA AIX CLI
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
{: #powerha-api-key-cli}

Manage apikey.

```sh
ibmcloud power-hadr powerhasm api-key --help
```

### `ibmcloud power-hadr powerhasm api-key get`
{: #powerha-api-key-get}

Retrieves existing apikey for the specified PowerHA service instance.

```sh
ibmcloud power-hadr powerhasm api-key get --instance-id INSTANCE-ID [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH]
```

#### Command options
{: #powerha-api-key-get-options}

`--instance-id` (string)
:   Unique identifier of the provisioned instance. Required.

`--accept-language` (string)
:   The language requested for the return document.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

#### Example

```sh
ibmcloud power-hadr powerhasm api-key get \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --accept-language en-US \
    --if-none-match abcdef
```

#### Example output

```json
{
  "id" : "12345",
  "api_key" : "abcd1234efgh5678ijkl9012"
}
```

### `ibmcloud power-hadr powerhasm api-key update`
{: #powerha-api-key-update}

Updates a new apikey for the specified PowerHA service instance.

```sh
ibmcloud power-hadr powerhasm api-key update --instance-id INSTANCE-ID [--api-key API-KEY] [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH]
```

#### Command options
{: #powerha-api-key-update-options}

`--instance-id` (string)
:   Unique identifier of the provisioned instance. Required.

`--api-key` (string)
:   The API key to be stored or registered.

`--accept-language` (string)
:   The language requested for the return document.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

#### Example

```sh
ibmcloud power-hadr powerhasm api-key update \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --api-key adfadfdsafsdfdsf \
    --accept-language en-US \
    --if-none-match abcdef
```

#### Example output

```json
{
  "description" : "API key created successfully",
  "example" : "adfadfdsafsdfdsf",
  "id" : "12345",
  "api_key" : "abcd1234efgh5678ijkl9012"
}
```

## Cluster Node
{: #powerha-cluster-node-cli}

Manage the PowerHA cluster node configuration.

```sh
ibmcloud power-hadr powerhasm cluster-node --help
```

### `ibmcloud power-hadr powerhasm cluster-node get`
{: #powerha-cluster-node-get}

Retrieves details of all cluster nodes configured for the given PowerHA service instance.

```sh
ibmcloud power-hadr powerhasm cluster-node get --instance-id INSTANCE-ID [--if-none-match IF-NONE-MATCH]
```

#### Command options
{: #powerha-cluster-node-get-options}

`--instance-id` (string)
:   Unique identifier of the provisioned instance. Required.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

#### Example

```sh
ibmcloud power-hadr powerhasm cluster-node get \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --if-none-match abcdef
```

#### Example output

```json
{
  "id" : "123498690689",
  "primary_node_details" : [ { ... } ],
  "secondary_node_details" : [ { ... } ]
}
```

## Deployment
{: #powerha-deployment-cli}

Manage PowerHA deployments.

```sh
ibmcloud power-hadr powerhasm deployment --help
```

### `ibmcloud power-hadr powerhasm deployment get`
{: #powerha-deployment-get}

Retrieves the PowerHA deployment configuration and status.

```sh
ibmcloud power-hadr powerhasm deployment get --instance-id INSTANCE-ID [--if-none-match IF-NONE-MATCH]
```

#### Command options
{: #powerha-deployment-get-options}

`--instance-id` (string)
:   Unique identifier of the provisioned instance. Required.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

#### Example

```sh
ibmcloud power-hadr powerhasm deployment get \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6 \
    --if-none-match abcdef
```

#### Example output

```json
{
  "cloud_account_id" : "cloud-acc-0001",
  "connectivity_type" : "vpc",
  "status" : "completed"
}
```

## Event
{: #powerha-event-cli}

Shows events generated during PowerHA operations.

```sh
ibmcloud power-hadr powerhasm event --help
```

### `ibmcloud power-hadr powerhasm event list`
{: #powerha-event-list}

Retrieves events for the specified service instance.

```sh
ibmcloud power-hadr powerhasm event list --instance-id INSTANCE-ID
```

#### Example

```sh
ibmcloud power-hadr powerhasm event list \
    --instance-id 8eefautr-4c02-0009-0086-8bd4d8cf61b6
```

#### Example output

```json
{
  "events" : [ { ... } ]
}
```

## Agent
{: #powerha-agent-cli}

Manage PowerHA agent operations.

```sh
ibmcloud power-hadr powerhasm agent --help
```

### `ibmcloud power-hadr powerhasm agent download`
{: #powerha-agent-download}

Downloads the PowerHA agent.

```sh
ibmcloud power-hadr powerhasm agent download --instance-id INSTANCE-ID --vm-name VM-NAME
```

## PowerVS Workspaces
{: #powerha-workspaces-cli}

Retrieves PowerVS workspaces.

```sh
ibmcloud power-hadr powerhasm powervs-workspaces --instance-id INSTANCE-ID --location-id LOCATION-ID
```

## Locations
{: #powerha-locations-cli}

Retrieves supported PowerVS locations.

```sh
ibmcloud power-hadr powerhasm locations --instance-id INSTANCE-ID
```

## Last Operation
{: #powerha-last-operation-cli}

Retrieves the most recent operation performed on the service instance.

```sh
ibmcloud power-hadr powerhasm last-operation --instance-id INSTANCE-ID
```
