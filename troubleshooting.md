---
copyright:
  years: 2025
lastupdated: "2025-11-20"

subcollection: dr-automation-powervs

keywords: troubleshooting, API key, DR automation

---
# Troubleshooting

## Why can't I rotate the API key?  
{: #rotate-api-key}  
{: troubleshoot}  

### What's happening  
The user is unable to regenerate the API key, which is required to maintain secure access to the service.  

### Why it's happening  
The API key might be expired or improperly configured, leading to a failure in regenerating it.  

### How to fix it  
{: tsResolve}  
1. Access the **External orchestrator GUI**.  
2. Navigate to the **Policies** tab from the top navigation bar.  
3. Locate the **API Key** field in the list of tunable attributes.  
4. Click **Regenerate** to create a new API key.  
5. Save the changes to securely apply the new key.  

## How does the service work?  
{: #how-service-works}  
{: troubleshoot}  

### What's happening  
Users are unclear about how the service automates disaster recovery operations.  

### Why it's happening  
The architecture and components of the service may not be fully understood.  

### How to fix it  
{: tsResolve}  
- The service automates failover and failback processes across sites.  
- The **Service Broker** manages resource provisioning and billing.  
- The **KSYS orchestrator** handles VM orchestration, ensuring resources are activated in the correct sequence.  
- **Global Replication Services (GRS)** facilitates data replication between primary and backup sites.  
- Users can configure and monitor the DR environment through the **IBM Cloud GUI** and manage VMs via the **External orchestrator UI**.  

## Why am I unable to perform IAM actions with the service?  
{: #iam-actions}  
{: troubleshoot}  

### What's happening  
IAM actions, such as assigning roles or monitoring permissions, are not functioning as expected.  

### Why it's happening  
This issue occurs due to insufficient permissions or improper configurations in the IAM roles that are assigned to the service.  

### How to fix it  
{: tsResolve}  
1. Log in to the **IAM Console** via the IBM Cloud portal.  
2. Review the roles that are assigned to the DR automation service under the **Access Groups** tab.  
3. Enable **Activity Tracker** under the **Monitoring** tab to track IAM actions.  
4. Simulate an IAM action (for example, assigning a role) and check logs in the **Activity Tracker** for details.  
5. If issues persist, rotate the API key in the **Policies** tab by clicking **Regenerate** and save the changes.  

## Why is there an error retrieving the access token during provisioning?  
{: #access-token-error}  
{: troubleshoot}  

### What's happening  
The provisioning process fails with the error message:  
> `Error getting access token.`  

### Why it's happening  
The service is unable to authenticate due to an expired or invalid API key, or insufficient IAM permissions.  

### How to fix it  
{: tsResolve}  
1. Access the **DR Automation GUI**.  
2. Navigate to the **Policies** tab.  
3. Verify that the API key is valid and not expired.  
4. Regenerate the API key by clicking **Regenerate**, then save the changes.  
5. Confirm that IAM roles and permissions for the DR automation service are correctly assigned.  
6. Retry the provisioning operation and monitor the logs for success.  

## Why does the "orchestrator password format is incorrect" error occur?  
{: #password-format-error}  
{: troubleshoot}  

### What's happening  
The system displays an error indicating the orchestrator password does not meet format requirements.  

### Why it's happening  
The password that is provided does not comply with the security standards that are required by the orchestrator.  

### How to fix it  
{: tsesolve}  
1. Access the **DR Automation GUI**.  
2. Navigate to the **Policies** tab.  
3. Locate the **Orchestrator Password** field under tunable attributes.  
4. Update the password to meet these requirements:  
   - At least 8 characters.  
   - A mix of uppercase and lowercase letters.  
   - At least one number and one special character (for example, @, #, $).  
5. Save the changes and retry the update operation.  

## Why am I unable to delete the provisioned disaster recovery service?  
{: #delete-service-error}  
{: troubleshoot}  

### What's happening  
The system fails to delete the provisioned service, displaying a generic error message:  
> `Provision disaster recovery service deletion failed.`  

### Why it's happening  
Dependencies, such as active VMs or storage volumes, may prevent the service from being deleted, or the API key may be invalid.  

### How to fix it  
{: tsResolve}  
1. Access the **DR Automation GUI**.  
2. Navigate to the **Events** tab and review the detailed logs.  
3. Verify API connectivity by running a test command (for example, ping or curl) to the service endpoint.  
4. Check for active resources that are associated with the service and ensure that there are no dependencies.  
5. Regenerate the API key from the **Policies** tab and update the system with the new key.  
6. Retry the delete operation and monitor for success.  

## Why is the **Finish** button not enabled in the UI after orchestrator deployment ?  
{: #orch-fini-enab}  
{: troubleshoot}  

### What's happening
{: #select-dr-loc}  
The **Finish** button in the UI remains disabled, preventing you from starting the External Orchestrator UI.  

### Why it's happening
{: #select-dr-locat}

Once the orchestrator VM is deployed and active, the cluster configuration starts automatically. Once it is completed, KSYS sends an event, and the UI enables the **Finish** button to start the external orchestrator UI.

If there are any communication issues preventing the orchestrator VM from sending the event, the **Finish** button is not enabled, and you will not be able to enable DR for managed VM's using the External Orchestrator UI.

### How to fix it  
{: tsResolve}  

1. Log in to the orchestrator VM from the IBM Cloud UI or through the jump server VSI created during the VPC landing zone deployment.

2. Validate the communication using the following link:

> `curl -v power-dra.cloud.ibm.com`

   OR

> `curl -v www.google.com`


3. Export the proxy server IP configured on Edge VSI that is created through the VPC landing zone and perform the step two to check the communication.

   `export http_proxy="<proxy_ip:port>"`

   `export https_proxy="<proxy_ip:port>"`

   **Example:**

   `export http_proxy="10.30.10.4:3128"`

   `export https_proxy="10.30.10.4:3128"`

If the communication issue persists, you can check the status of the squid service on Edge VSI.

- To check the squid proxy status, run the following command on the Edge VSI server

   > `systemctl status squid`

- If the service is not active, run the following command to restart the squid service

   > `systemctl restart squid`

  For more information, refer to [Power Virtual Server with VPC landing zone](/docs/deployable-reference-architectures?topic=deployable-reference-architectures-deploy-arch-ibm-pvs-inf-standard).

## Why is the Orchestrator external connectivity status shown as inactive?
{: #oe-xe-csi}  
{: troubleshoot} 

 ### What's happening
 {: tsressolve} 

The External Connectivity status of the Orchestrator appears as Inactive in the UI.

 ### Why it's happening
 {: why-it hap}

The Orchestrator is unable to establish a connection with any IBM Cloud services, which prevents it from effectively managing failover scenarios in the event of a workload failure.

 ### How to fix it
 {: fix-it}

Refer to the topic [How to fix it](#how-to-fix-it-7) for guidance on resolving the inactive state of the Orchestrator's external connectivity.

## Why are no workspaces listed after selecting Client location?
{: #select-dr-loca}
{: troubleshoot}

### What's happening
{: #select-dr-locatio}

The user is unable to select a Disaster Recovery location or does not see any workspaces listed in the external orchestrator UI.

### Why it's happening
{: #select-dr-loca}

This issue occurs when no PowerVS workspace is available in the selected location, preventing the provisioning of a Managed VM for disaster recovery.

### How to fix it
{: tsResolve-fix}

1. In the external orchestrator UI, go to the section where you configure the DR plan.

2. From the Disaster Recovery Location drop-down list, select either IBM Cloud or Client location.

3. If you select Client location, ensure that you have at least one PowerVS workspace available in your location.

4. After selecting the plan, wait for the list of available workspaces to appear.

5. From the list, choose the appropriate workspace and enable the workload you want to protect with disaster recovery.

## why does a simultaneous deployments fails when using the same PowerVS workspace?
{: #ksys-image-deploy}  
{: troubleshoot}

### What's happening

During a DR Automation deployment, the KSYS image is downloaded to the selected workspace where the orchestrator is to be created. Once the deployment is completed, this image is automatically deleted.

If the same workspace is used for a subsequent deployment, the image download is not re-initiated because the system detects that the image previously existed. Since the image may have been deleted during the first deployment, the second deployment can fail when creating the orchestrator.

### Why it's happening

The system assumes the KSYS image already exists in the workspace and skips downloading it. If the image was removed after the first deployment, the orchestrator creation cannot proceed.

### How to fix it
{: tsResolve}

1. Redeploy the DR Automation environment and ensure the KSYS image is downloaded successfully.  
2. Avoid performing multiple deployments simultaneously in the same workspace to prevent deployment failures.

**Recommendation:** Perform sequential deployments using separate workspaces or wait until the first deployment completes before starting a new one.
