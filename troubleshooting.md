---
copyright:
  years: 2025
lastupdated: "2025-03-06"

subcollection: dr-automation

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
1. Access the **VM Recovery Manager DR GUI**.  
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
- Users can configure and monitor the DR environment through the **IBM Cloud GUI** and manage VMs via the **VM Recovery Manager HA/DR interface**.  

## Why am I unable to perform IAM actions with the service?  
{: #iam-actions}  
{: troubleshoot}  

### What's happening  
IAM actions, such as assigning roles or monitoring permissions, are not functioning as expected.  

### Why it's happening  
This issue occurs due to insufficient permissions or improper configurations in the IAM roles assigned to the service.  

### How to fix it  
{: tsResolve}  
1. Log in to the **IAM Console** via the IBM Cloud portal.  
2. Review the roles assigned to the DR automation service under the **Access Groups** tab.  
3. Enable **Activity Tracker** under the **Monitoring** tab to track IAM actions.  
4. Simulate an IAM action (e.g., assigning a role) and check logs in the **Activity Tracker** for details.  
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
The password provided does not comply with the security standards required by the orchestrator.  

### How to fix it  
{: tsesolve}  
1. Access the **DR Automation GUI**.  
2. Navigate to the **Policies** tab.  
3. Locate the **Orchestrator Password** field under tunable attributes.  
4. Update the password to meet these requirements:  
   - At least 8 characters.  
   - A mix of uppercase and lowercase letters.  
   - At least one number and one special character (e.g., @, #, $).  
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
3. Verify API connectivity by running a test command (e.g., ping or curl) to the service endpoint.  
4. Check for active resources associated with the service and ensure there are no dependencies.  
5. Regenerate the API key from the **Policies** tab and update the system with the new key.  
6. Retry the delete operation and monitor for success.  

## Why is the **Finish** button not enabled in the UI after orchestrator deployment?  
{: #orch-fini-enab}  
{: troubleshoot}  

### What's happening  
The **Finish** button in the UI remains disabled, preventing you from launching the External Orchestrator UI.  

### Why it's happening  
After the orchestrator VM is deployed and active, the cluster configuration starts automatically. Once completed, KSYS sends an event to enable the **Finish** button. However, if there is a communication issue preventing the orchestrator VM from sending this event, the button remains disabled, and you cannot add managed VMs using the External Orchestrator UI.  

### How to fix it  
{: tsResolve}  

1. Log in to the **Orchestrator VM** from the IBM Cloud UI or through the VPC-created jump server.  
2. Export the proxy IP that was created through the VPC landing zone:

  > **export**

  `http_proxy="<proxy_ip:port>"`
  `https_proxy="<proxy_ip:port>"`
  

   **Example:**

   > **Export**:
   `http_proxy="10.30.10.4:3128"`
   `https_proxy="10.30.10.4:3128"`

3. Validate the communication using the below link:

   `curl -v` [www.google.com](www.google.com).
