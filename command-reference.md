---
copyright:
  years: 2025
lastupdated: "2025-12-03"

subcollection: dr-automation-powervs

keywords: power-hadr, cli, pdr

---


# {{site.data.keyword.DR_full}} CLI version 0.0.1
{: #dr-automation-cli-version}




## Available Commands:
{: #avalible-cmd}


`api-key`- Manage the API key for the Power DR Automation service instance.  
`event`- View events generated during DR Automation operations such as provisioning, ManageDR creation, image download, virtual server creation, orchestrator cluster creation, and API key updates.  
`grs-location-pairs`- Retrieve the Global Replication Services (GRS) location pairs associated with the specified service instance based on managed VMs.  
`locations`- List the available disaster recovery (DR) locations for the specified service instance.  
`managed-vms`- Retrieve the list of disaster recovery managed virtual machines for the specified service instance.  
`summary`- Retrieve a consolidated disaster recovery summary for the service instance, including orchestrator details, service configuration, and managed VM information.  
`machine-types`- List the supported machine types available for disaster recovery for the specified primary and standby workspaces.  
`powervs-workspaces`- Retrieve the Power Virtual Server workspaces for the primary and standby orchestrators based on the specified location ID.  
`create`- Create and deploy the orchestrator virtual machine in the specified workspace and configuration to manage disaster recovery.  
`last-operation`- Retrieve the status and details of the most recent operation performed on the specified service instance, such as provisioning, updating, or deprovisioning.  



## Api key
{: #power-hadr-api-key-cli}

Manage apikey

```sh
ibmcloud power-hadr pdr api-key --help
```


### `ibmcloud power-hadr pdr api-key update`
{: #power-hadr-cli-api-key-update-command}

Updating the current API key details for the specified service instance.

```sh
ibmcloud power-hadr pdr api-key update --instance-id INSTANCE-ID --api-key API-KEY [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH]
```


#### Command options
{: #power-hadr-api-key-update-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

`--api-key` (string)
:   The new API key value that will replace the existing one. Required.

`--accept-language` (string)
:   The language requested for the return document.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

#### Example
{: #power-hadr-api-key-update-examples}

```sh
ibmcloud power-hadr pdr api-key update \
    --instance-id crn:v1:staging:public:power-dr-automation:global:a/a123456fb04ceebfb4a9fd38c22334455:123456d3-1122-3344-b67d-4389b44b7bf9:: \
    --api-key adfadfdsafsdfdsf \
    --accept-language exampleString \
    --if-none-match exampleString
```


#### Example output
{: #power-hadr-api-key-update-cli-output}

```json
{
  "description" : "Key is valid.",
  "status" : "Active"
}
```


## Event
{: #power-hadr-event-cli}

Shows event that got generated during various DR Automation operations such as provision creation, ManageDR Creation, image download, virtual server instance creation, orchestrator cluster creation, API Key updation along with their corresponding actions and descriptions.

```sh
ibmcloud power-hadr pdr event --help
```


### `ibmcloud power-hadr pdr event list`
{: #power-hadr-cli-event-list-command}

Retrieves the list of events from the specified service instance ID.

```sh
ibmcloud power-hadr pdr event list --instance-id INSTANCE-ID [--time TIME] [--from-time FROM-TIME] [--to-time TO-TIME] [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH]
```


#### Command options
{: #power-hadr-event-list-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

`--time` (string)
:   (deprecated - use from_time) A time in either ISO 8601 or unix epoch format.

`--from-time` (string)
:   A from query time in either ISO 8601 or unix epoch format.

`--to-time` (string)
:   A to query time in either ISO 8601 or unix epoch format.

`--accept-language` (string)
:   The language requested for the return document.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

#### Example
{: #power-hadr-event-list-examples}

```sh
ibmcloud power-hadr pdr event list \
    --instance-id crn:v1:staging:public:power-dr-automation:global:a/a123456fb04ceebfb4a9fd38c22334455:123456d3-1122-3344-b67d-4389b44b7bf9:: \
    --time 2025-06-19T23:59:59Z \
    --from-time 2025-06-19T00:00:00Z \
    --to-time 2025-06-19T23:59:59Z \
    --accept-language exampleString \
    --if-none-match exampleString
```


#### Example output
{: #power-hadr-event-list-cli-output}

```json
{
  "events" : [ {
    "action" : "create",
    "event_id" : "1cecfe43-43cd-4b1b-86be-30c2d3d2a25f",
    "level" : "info",
    "message" : "Service Instance '7222c899-a31a-4a0c-be03-75920d23cd16' has been created successfully.",
    "messageData" : {
      "InstanceID" : {
        "id" : "7222c899-a31a-4a0c-be03-75920d23cd16"
      }
    },
    "metadata" : { },
    "resource" : "ProvisionID",
    "time" : "2025-06-23T07:12:49.840Z",
    "timestamp" : "1750662769",
    "user" : {
      "user_id" : "admin"
    }
  }, {
    "action" : "create",
    "event_id" : "c49f0ced-2a78-48a6-929c-6b824555ddc6",
    "level" : "info",
    "message" : "Disaster recovery for Service Instance '7222c899-a31a-4a0c-be03-75920d23cd16' has been managed successfully.",
    "messageData" : {
      "InstanceID" : {
        "id" : "7222c899-a31a-4a0c-be03-75920d23cd16"
      }
    },
    "metadata" : { },
    "resource" : "managedr",
    "time" : "2025-06-23T07:14:53.871Z",
    "timestamp" : "1750662893",
    "user" : {
      "email" : "abcuser@ibm.com",
      "user_id" : "IBMid-695000ab7E"
    }
  } ]
}
```


### ```ibmcloud power-hadr pdr event get```
{: #power-hadr-cli-event-get-command}

Retrieves the details of a specific event for the given service instance provision ID.

```sh
ibmcloud power-hadr pdr event get --instance-id INSTANCE-ID --event-id EVENT-ID [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH]
```


#### Command options
{: #power-hadr-event-get-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

`--event-id` (string)
:   Event ID. Required.

`--accept-language` (string)
:   The language requested for the return document.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

#### Example
{: #power-hadr-event-get-examples}

```sh
ibmcloud power-hadr pdr event get \
    --instance-id crn:v1:staging:public:power-dr-automation:global:a/a123456fb04ceebfb4a9fd38c22334455:123456d3-1122-3344-b67d-4389b44b7bf9:: \
    --event-id 00116b2a-9326-4024-839e-fb5364b76898 \
    --accept-language exampleString \
    --if-none-match exampleString
```


#### Example output
{: #power-hadr-event-get-cli-output}

```json
{
  "action" : "create",
  "api_source" : "dr-automation-api",
  "event_id" : "1cecfe43-43cd-4b1b-86be-30c2d3d2a25f",
  "level" : "info",
  "message" : "Service Instance created successfully",
  "message_data" : {
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
  "timestamp" : "1750662769",
  "user" : {
    "user_email" : "example.user@ibm.com",
    "user_id" : "IBMid-123456"
  }
}
```


## GRS location pairs
{: #power-hadr-dr-grs-location-pairs}

### `ibmcloud power-hadr pdr grs-location-pairs`
{: #power-hadr-cli-grs-location-pairs-command}

Retrieves the (GRS) location pairs associated with the specified service instance based on managed VMs.

```sh
ibmcloud power-hadr pdr grs-location-pairs --instance-id INSTANCE-ID [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH]
```


#### Command options
{: #power-hadr-grs-location-pairs-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

`--accept-language` (string)
:   The language requested for the return document.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

#### Example
{: #power-hadr-grs-location-pairs-examples}

```sh
ibmcloud power-hadr pdr grs-location-pairs \
    --instance-id crn:v1:staging:public:power-dr-automation:global:a/a123456fb04ceebfb4a9fd38c22334455:123456d3-1122-3344-b67d-4389b44b7bf9:: \
    --accept-language exampleString \
    --if-none-match exampleString
```


## DR locations
{: #power-hadr-dr-locations}

### `ibmcloud power-hadr pdr locations`
{: #power-hadr-cli-locations-command}

Retrieves the list of disaster recovery (DR) locations available for the specified service instance.

```sh
ibmcloud power-hadr pdr locations --instance-id INSTANCE-ID [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH]
```


#### Command options
{: #power-hadr-locations-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

`--accept-language` (string)
:   The language requested for the return document.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

#### Example
{: #power-hadr-locations-examples}

```sh
ibmcloud power-hadr pdr locations \
    --instance-id crn:v1:staging:public:power-dr-automation:global:a/a123456fb04ceebfb4a9fd38c22334455:123456d3-1122-3344-b67d-4389b44b7bf9:: \
    --accept-language exampleString \
    --if-none-match exampleString
```


#### Example output
{: #power-hadr-locations-cli-output}

```json
{
  "dr_locations" : [ {
    "id" : "loc-001",
    "name" : "us-south"
  }, {
    "id" : "loc-002",
    "name" : "eu-de"
  } ]
}
```


## Managed VM's
{: #power-hadr-dr-managed-vms}

### `ibmcloud power-hadr pdr managed-vms`
{: #power-hadr-cli-managed-vms-command}

Retrieves the list of disaster recovery (DR) managed virtual machines for the specified service instance.

```sh
ibmcloud power-hadr pdr managed-vms --instance-id INSTANCE-ID [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH]
```


#### Command options
{: #power-hadr-managed-vms-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

`--accept-language` (string)
:   The language requested for the return document.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

#### Example
{: #power-hadr-managed-vms-examples}

```sh
ibmcloud power-hadr pdr managed-vms \
    --instance-id crn:v1:staging:public:power-dr-automation:global:a/a123456fb04ceebfb4a9fd38c22334455:123456d3-1122-3344-b67d-4389b44b7bf9:: \
    --accept-language exampleString \
    --if-none-match exampleString
```


#### Example output
{: #power-hadr-managed-vms-cli-output}

```json
{
  "managed_vm_list" : {
    "3f2e1a09-1234-4d56-7890-abcd1234ef56" : {
      "core" : "0.50",
      "dr_average_time" : "10",
      "dr_region" : "nyc02",
      "memory" : "4",
      "region" : "nyc01",
      "vm_name" : "example_vm",
      "workgroup_name" : "Example_Workgroup",
      "workspace_name" : "Example_Workspace"
    },
    "9b8a7c65-4321-0fed-cba9-87654321abcd" : {
      "core" : "1.00",
      "dr_average_time" : "5",
      "dr_region" : "sfo04",
      "memory" : "8",
      "region" : "sfo03",
      "vm_name" : "another_vm",
      "workgroup_name" : "Another_Workgroup",
      "workspace_name" : "Another_Workspace"
    }
  }
}
```



## DR summary
{: #power-hadr-dr-summary}

### `ibmcloud power-hadr pdr summary`
{: #power-hadr-cli-summary-command}

Retrieves the disaster recovery (DR) summary details for the specified service instance, including key configuration, status information and managed vm details.

```sh
ibmcloud power-hadr pdr summary --instance-id INSTANCE-ID [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH]
```


#### Command options
{: #power-hadr-summary-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

`--accept-language` (string)
:   The language requested for the return document.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

#### Example
{: #power-hadr-summary-examples}

```sh
ibmcloud power-hadr pdr summary \
    --instance-id crn:v1:staging:public:power-dr-automation:global:a/a123456fb04ceebfb4a9fd38c22334455:123456d3-1122-3344-b67d-4389b44b7bf9:: \
    --accept-language exampleString \
    --if-none-match exampleString
```


#### Example output
{: #power-hadr-summary-cli-output}

```json
{
  "managed_vm_list" : [ {
    "id" : "vm-01-1234-5678-90ab",
    "name" : "test-aix-vm1"
  }, {
    "id" : "vm-02-2234-5678-90cd",
    "name" : "test-aix-vm2"
  } ],
  "orchestrator_details" : {
    "location_id" : "dal10",
    "mfa_enabled" : "false",
    "orch_ext_connectivity_status" : "Connected",
    "orch_standby_node_addition_status" : "Success",
    "orchestrator_cluster_message" : "Cluster operational",
    "orchestrator_config_status" : "Configured",
    "orchestrator_group_leader" : "primary0906",
    "orchestrator_location_type" : "off-premises",
    "orchestrator_name" : "primary0906",
    "orchestrator_status" : "Active",
    "orchestrator_workspace_name" : "vpcdr6-abc-power-workspace",
    "proxy_ip" : "10.0.0.5",
    "schematic_workspace_name" : "us-south.workspace.projects-service.3ae96a02",
    "schematic_workspace_status" : "Available",
    "ssh_key_name" : "mani_key",
    "standby_orchestrator_name" : "standby0906",
    "standby_orchestrator_status" : "Active",
    "standby_orchestrator_workspace_name" : "Test_workspace_frankfurt",
    "transit_gateway_name" : "dra-tg-01",
    "vpc_name" : "vpc-primary-us-south"
  },
  "service_details" : {
    "crn" : "crn:v1:staging:public:power-dr-automation:global:a/b68c234e719144b18598ae4a7b80c44c:03e32707-1234-zzsd-kkjh-4d790e863d5a09061::",
    "deployment_name" : "defect_testing6abc0906",
    "description" : "5/5: Primary orchestrator primary0906 is successfully deployed in 3m17s",
    "orchestrator_ha" : true,
    "primary_ip_address" : "10.51.0.123",
    "primary_orchestrator_dashboard_url" : "",
    "recovery_location" : "eu-de",
    "resource_group" : "default-rg",
    "standby_description" : "4/4: Standby orchestrator standby0906 is successfully deployed in 5m37s",
    "standby_ip_address" : "10.0.9.123",
    "standby_orchestrator_dashboard_url" : "",
    "standby_status" : "Active",
    "status" : "Active"
  }
}
```


## Machine types
{: #power-hadr-dr-machine-types}

### `ibmcloud power-hadr pdr machine-types`
{: #power-hadr-cli-machine-types-command}

Retrieves the list of supported machine types for the given workspace. This endpoint is used to identify machine types available for disaster recovery automation.

```sh
ibmcloud power-hadr pdr machine-types --instance-id INSTANCE-ID --primary-workspace-name PRIMARY-WORKSPACE-NAME [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH] [--standby-workspace-name STANDBY-WORKSPACE-NAME]
```


#### Command options
{: #power-hadr-machine-types-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

`--primary-workspace-name` (string)
:   The primary Power virtual server workspace name. Required.

`--accept-language` (string)
:   The language requested for the return document.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

`--standby-workspace-name` (string)
:   The standby Power virtual server workspace name.

#### Example
{: #power-hadr-machine-types-examples}

```sh
ibmcloud power-hadr pdr machine-types \
    --instance-id crn:v1:staging:public:power-dr-automation:global:a/a123456fb04ceebfb4a9fd38c22334455:123456d3-1122-3344-b67d-4389b44b7bf9:: \
    --primary-workspace-name Test-workspace-wdc06 \
    --accept-language exampleString \
    --if-none-match exampleString \
    --standby-workspace-name Test-workspace-wdc07
```



## powervs workspaces
{: #power-hadr-dr-powervs-workspaces}

### `ibmcloud power-hadr pdr powervs-workspaces`
{: #power-hadr-cli-powervs-workspaces-command}

Retrieves the power virtual server workspaces for primary and standby orchestrator based on location id.

```sh
ibmcloud power-hadr pdr powervs-workspaces --instance-id INSTANCE-ID --location-id LOCATION-ID [--if-none-match IF-NONE-MATCH]
```

#### Command options
{: #power-hadr-powervs-workspaces-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

`--location-id` (string)
:   Location ID value. Required.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

#### Example
{: #power-hadr-powervs-workspaces-examples}

```sh
ibmcloud power-hadr pdr powervs-workspaces \
    --instance-id crn:v1:staging:public:power-dr-automation:global:a/a123456fb04ceebfb4a9fd38c22334455:123456d3-1122-3344-b67d-4389b44b7bf9:: \
    --location-id exampleString \
    --if-none-match exampleString
```


#### Example output
{: #power-hadr-powervs-workspaces-cli-output}

```json
{
  "dr_standby_workspaces" : [ {
    "details" : {
      "crn" : "crn:v1:bluemix:public:power-iaas:us-south:abc123:8aac93a4-f0cf-4b19-8d6d-9ba10883985d::"
    },
    "id" : "8aac93a4-f0cf-4b19-8d6d-9ba10883985d",
    "location" : {
      "region" : "us-south",
      "type" : "region",
      "url" : "https://us-south.power-iaas.cloud.ibm.com"
    },
    "name" : "ws-dallas-standby",
    "status" : "active"
  } ],
  "dr_workspaces" : [ {
    "details" : {
      "crn" : "crn:v1:bluemix:public:power-iaas:us-south:abc123:9a9688a8-57e1-40b5-8c7d-f07e0a1cb305::"
    },
    "id" : "9a9688a8-57e1-40b5-8c7d-f07e0a1cb305",
    "location" : {
      "region" : "us-south",
      "type" : "region",
      "url" : "https://us-south.power-iaas.cloud.ibm.com"
    },
    "name" : "ws-dallas-primary",
    "status" : "active"
  } ]
}
```


## Create manage DR
{: #power-hadr-dr-create}

### `ibmcloud power-hadr pdr create`
{: #power-hadr-cli-create-command}

Creates Orchestrator VM in the given workspace and configuration. Orchestrator VM can be used to manage multiple virtual servers and help ensure continuous availability. For more details, refer Deploying the Orchestrator - /docs/dr-automation-powervs?topic=dr-automation-powervs-idep-the-orch.

```sh
ibmcloud power-hadr pdr create --instance-id INSTANCE-ID [--api-key API-KEY] [--client-id CLIENT-ID] [--client-secret CLIENT-SECRET] [--guid GUID] [--location-id LOCATION-ID] [--machine-type MACHINE-TYPE] [--orchestrator-ha=ORCHESTRATOR-HA] [--orchestrator-location-type ORCHESTRATOR-LOCATION-TYPE] [--orchestrator-name ORCHESTRATOR-NAME] [--orchestrator-password ORCHESTRATOR-PASSWORD] [--orchestrator-workspace-id ORCHESTRATOR-WORKSPACE-ID] [--orchestrator-workspace-location ORCHESTRATOR-WORKSPACE-LOCATION] [--proxy-ip PROXY-IP] [--region-id REGION-ID] [--resource-instance RESOURCE-INSTANCE] [--secondary-workspace-id SECONDARY-WORKSPACE-ID] [--secret SECRET] [--secret-group SECRET-GROUP] [--ssh-key-name SSH-KEY-NAME] [--standby-machine-type STANDBY-MACHINE-TYPE] [--standby-orchestrator-name STANDBY-ORCHESTRATOR-NAME] [--standby-orchestrator-workspace-id STANDBY-ORCHESTRATOR-WORKSPACE-ID] [--standby-orchestrator-workspace-location STANDBY-ORCHESTRATOR-WORKSPACE-LOCATION] [--standby-tier STANDBY-TIER] [--tenant-name TENANT-NAME] [--tier TIER] [--stand-by-redeploy STAND-BY-REDEPLOY] [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH] [--accepts-incomplete=ACCEPTS-INCOMPLETE]
```


#### Command options
{: #power-hadr-create-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

`--api-key` (string)
:   The api Key of the service instance for deploying the disaster recovery service.

`--client-id` (string)
:   The Client Id created for MFA authentication API.

`--client-secret` (string)
:   The client secret created for MFA authentication API.

`--guid` (string)
:   The global unique identifier of the service instance.

`--location-id` (string)
:   The location or data center identifier where the service instance is deployed.

`--machine-type` (string)
:   The machine type used for deploying orchestrator.

`--orchestrator-ha` (bool)
:   Indicates whether the orchestrator High Availability (HA) is enabled for the service instance.

`--orchestrator-location-type` (string)
:   The cloud location where your orchestator need to be created.

`--orchestrator-name` (string)
:   The username used for the orchestrator.

`--orchestrator-password` (string)
:   The password that you can use to access your orchestrator.

`--orchestrator-workspace-id` (string)
:   The unique identifier orchestrator workspace.

`--orchestrator-workspace-location` (string)
:   The location of the orchestrator workspace.

`--proxy-ip` (string)
:   Proxy IP for the Communication between Orchestrator and Service broker.

`--region-id` (string)
:   The power virtual server region where the service instance is deployed.

`--resource-instance` (string)
:   The uniquie identifier of the associated IBM Cloud resource instance.

`--secondary-workspace-id` (string)
:   The unique identifier of the secondary workspace used for the disaster recovery.

`--secret` (string)
:   The secret name or identifier used for retrieving credentials from secrets manager.

`--secret-group` (string)
:   The secret group name in IBM Cloud Secrets Manager containing sensitive data for the service instance.

`--ssh-key-name` (string)
:   The name of the SSH key used for deploying the orchestator.

`--standby-machine-type` (string)
:   The machine type used for deploying standby virtual machines.

`--standby-orchestrator-name` (string)
:   The username for the standby orchestrator management interface.

`--standby-orchestrator-workspace-id` (string)
:   The unique identifier of the standby orchestrator workspace.

`--standby-orchestrator-workspace-location` (string)
:   The location of the standby orchestrator workspace.

`--standby-tier` (string)
:   The storage tier used for deploying standby orchestrator.

`--tenant-name` (string)
:   The tenant name for MFA authentication API.

`--tier` (string)
:   The storage tier used for deploying primary orchestrator.

`--stand-by-redeploy` (string)
:   Flag to indicate if standby should be redeployed (must be "true" or "false").

`--accept-language` (string)
:   The language requested for the return document.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

`--accepts-incomplete` (bool)
:   A value of true indicates that both the IBM Cloud platform and the requesting client support asynchronous deprovisioning.

    The default value is `true`.

#### Example
{: #power-hadr-create-examples}

```sh
ibmcloud power-hadr pdr create \
    --instance-id crn:v1:staging:public:power-dr-automation:global:a/a123456fb04ceebfb4a9fd38c22334455:123456d3-1122-3344-b67d-4389b44b7bf9:: \
    --api-key exampleString \
    --client-id abcd-97d2-1234-bf62-8eaecc67a1234 \
    --client-secret abcd1234xM1y123wK6qR9123456789bE2jG0pabcdefgh \
    --guid 123e4567-e89b-12d3-a456-426614174000 \
    --location-id dal10 \
    --machine-type bx2-4x16 \
    --orchestrator-ha=true \
    --orchestrator-location-type off-premises \
    --orchestrator-name adminUser \
    --orchestrator-password exampleString \
    --orchestrator-workspace-id orch-workspace-01 \
    --orchestrator-workspace-location us-south \
    --proxy-ip 10.40.30.10:8888 \
    --region-id us-south \
    --resource-instance crn:v1:bluemix:public:resource-controller::res123 \
    --secondary-workspace-id secondary-workspace789 \
    --secret exampleString \
    --secret-group default-secret-group \
    --ssh-key-name my-ssh-key \
    --standby-machine-type bx2-8x32 \
    --standby-orchestrator-name standbyAdmin \
    --standby-orchestrator-workspace-id orch-standby-02 \
    --standby-orchestrator-workspace-location us-east \
    --standby-tier Premium \
    --tenant-name xxx.ibm.com \
    --tier Standard \
    --stand-by-redeploy exampleString \
    --accept-language exampleString \
    --if-none-match exampleString \
    --accepts-incomplete=true
```


#### Example output
{: #power-hadr-create-cli-output}

```json
{
  "dashboard_url" : "https://power-dra.test.cloud.ibm.com/power-dra-ui?instance_id=crn:v1:bluemix:public:power-dr-automation:us-south:a/fe3c2ccd058e407c81e1dba2b5c0e0d6:e3d09875-bbf8-4d8a-b52c-abefb67a53c5::",
  "id" : "crn:v1:staging:public:power-dr-automation:global:a/a123456fb04ceebfb4a9fd38c22334455:123456d3-1122-3344-b67d-4389b44b7bf9::"
}
```


## Last Operation
{: #power-hadr-dr-last-operation}

### `ibmcloud power-hadr pdr last-operation`
{: #power-hadr-cli-last-operation-command}

Retrieves the status of the last operation performed on the specified service instance, such as provisioning, updating, or deprovisioning.

```sh
ibmcloud power-hadr pdr last-operation --instance-id INSTANCE-ID [--accept-language ACCEPT-LANGUAGE] [--if-none-match IF-NONE-MATCH]
```


#### Command options
{: #power-hadr-last-operation-cli-options}

`--instance-id` (string)
:   instance id of instance to provision. Required.

`--accept-language` (string)
:   The language requested for the return document.

`--if-none-match` (string)
:   ETag for conditional requests (optional).

#### Example
{: #power-hadr-last-operation-examples}

```sh
ibmcloud power-hadr pdr last-operation \
    --instance-id crn:v1:staging:public:power-dr-automation:global:a/a123456fb04ceebfb4a9fd38c22334455:123456d3-1122-3344-b67d-4389b44b7bf9:: \
    --accept-language exampleString \
    --if-none-match exampleString
```


#### Example output
{: #power-hadr-last-operation-cli-output}

```json
{
  "crn" : "crn:v1:staging:public:power-dr-automation:global:a/2c5d7270091f495795350e9adfa8399c:86e0c9a9-80f4-4fcf-88a0-07643de01bb8::",
  "deployment_name" : "dr-deployment-instance-1",
  "last_updated_orchestrator_deployment_time" : "2025-10-30T11:25:00Z",
  "last_updated_standby_orchestrator_deployment_time" : "2025-10-30T11:40:00Z",
  "mfa_enabled" : "false",
  "orch_ext_connectivity_status" : "Connected",
  "orch_standby_node_addtion_status" : "Completed",
  "orchestrator_cluster_message" : "Cluster healthy",
  "orchestrator_config_status" : "Configured",
  "orchestrator_ha" : true,
  "plan_name" : "standard",
  "primary_description" : "2/5: Creating primary orchestrator VM.",
  "primary_ip_address" : "192.168.1.10",
  "primary_orchestrator_status" : "orchestrator-VM-creation-in-progress",
  "recovery_location" : "us-east",
  "resource_group" : "Default",
  "standby_description" : "1/4: Service instance is downloading orchestrator image for standby VM creation.",
  "standby_ip_address" : "192.168.1.11",
  "standby_status" : "downloading-orchestrator-image",
  "status" : "Running"
}
```
