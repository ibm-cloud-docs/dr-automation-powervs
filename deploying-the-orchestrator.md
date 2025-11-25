---
copyright:
  years: 2025
lastupdated: "2025-11-25"

subcollection: dr-automation-powervs

keywords: deploying the orchestrator, 

---

# Deploying the orchestrator
{: #idep-the-orch}

After creating the resource, deploying the orchestrator for DR automation is essential to ensure that your Power Virtual Server environment is protected against disaster events. The orchestrator coordinates disaster recovery operations, including replication, failover, and failback of virtual machines. This screen displays high availability (HA) settings, authentication keys and resource allocation. Once deployed, the orchestrator can manage multiple virtual servers and help ensure continuous availability.
{:shortdesc: .shortdesc}

>**Note**:
>- The orchestrator VM is created with the default configuration of 0.5 CPU units and 4 GB memory.
>- This configuration is suitable for managing 30 PowerVS instances.
>- If you need to manage more than 30 Managed VMs, it is recommended to increase the configuration to 1 CPU unit and 6 GB of memory.
>- The DR automation displays notifications to keep you informed about important events such as deployment status, errors, or other operational updates. Notifications appear as pop-up messages on the screen with timestamp.

## Deploying the orchestrator for disaster recovery
{: #dep-the-orch-dis-re}

### Procedure 
{: #procedure}

To deploy the orchestrator with the necessary configurations to meet your disaster recovery requirements,
follow the steps:

1. After completing the **Create** resource step, you are redirected to the **Manage** tab to proceed with the deployment.
2. In the **Orchestrator HA** section, click **Enable** to configure both a primary and standby orchestrator in high availability mode, or click **Disable** to configure only the primary orchestrator.
3. In the Configure primary orchestrator section, enter the **DR Orchestrator name**.

4. Set a password in the **DR Orchestrator password** field and re-enter the password in **Confirm DR orchestrator password** section to secure access to the external orchestrator interface.
   > **Note**: This password is set for the Orchestrator VM, and you can use it to login to the Orchestrator VM UI.

5. Provide a valid **IBM Cloud API key**.
   > **Note**: Enter your API key, which is required to access various services described in [Access role requirements for Power Virtual Server DR Automation](/docs/dr-automation-powervs?topic=dr-automation-powervs-iam-manage#ser-acc-role-dr-auto). Can ensure that the API key has the necessary permissions for proper functions.

6. The **Location Type** field is selected by default.

7. In the **DR location** field, select the target region for deploying the orchestrator VM.

    > **Note**: If you select **Chennai (in-che)** or **Montréal (ca-mon)** for the primary or standby (secondary) workspace, you must provide proxy details in the **Advanced configuration** section. These regions require a proxy for orchestrator communication with IBM Cloud services.

8. Select the **DR Power Virtual Server workspace** that is listed based on the selected **DR location**.
9. To create ksys VM with secrets, click **Select from Secrets Manager** and select **Service Instances**, **Secret Groups**, and **Secrets** or disable the  **Use a secret** radio button and select the SSH key from **SSH key name**.

    > **Note**: The SSH Key dropdown displays only the Account level SSH-keys.

10. In **Configure standby orchestrator (for HA)**, enter the **Standby orchestrator name** and select a **Standby Power Virtual Server workspace** to define the Power Virtual Server workspace in which the standby orchestrator is deployed, when Orchestrator HA is enabled in config page. These settings enable the orchestrator to provide continuous recovery capabilities if the primary site fails.

11. (Optional) Expand the **Advanced configuration** to configure Multi Factor Authentication (MFA).


    > **Prerequisite**: To Enable MFA, you must complete the MFA tenant setup and obtain the **Client ID**, **Client Secret**, and **Tenant Name** from [IBM Security Verify](https://www.ibm.com/account/reg/us-en/signup?formid=urx-30041&_ga=2.41335909.671467744.1669106438-1806696627.1657020197).
    > - For more information on MFA configuration, see [Setting up Multifactor Authentication](/docs/dr-automation-powervs?topic=dr-automation-powervs-multifactor-authentication).
    > - Select the **Enable MFA** checkbox and enter the **Client ID**, **Client Secret**, and **Tenant Name** that you generated during the MFA tenant setup. When deployment completes, the orchestrator is registered with IBM Security Verify.
    > - The root user is prompted to enter their password first and then an OTP during the first login.
    > - **Note:** MFA status is displayed in the **Orchestrator Details** page and MFA events are captured in the **Events** log for auditing.

12. Enter the proxy details if you have selected **Chennai (in-che, che01)** or **Montréal (ca-mon)** as the DR location. For more information, see [How to get ProxyIP details which is configured for Virtual Server Instance for VPC](https://test.cloud.ibm.com/docs-draft/dr-automation-powervs?topic=dr-automation-powervs-faqs#vpc-vsi-enab).

13. (Optional) Expand the **Advanced configuration** to change the Storage tier and Machine type configuration based on the **Orchestrator HA** selection.

14. After verifying all settings, click **Deploy orchestrator** to start the deployment process, which creates the orchestrator VMs.

14. **Finish** button is enabled once the orchestrator VM is deployed and now Click **Finish** to complete the setup.

15. Configure and manage the Power Virtual Server instances through the **External orchestrator interface** for disaster recovery.

  >**Note**: The orchestrator interface (UI) is launched at https://`<Orchestrator IP>`:3000/login. The `<Orchestrator IP>` address is the system on which the orchestrator UI is installed and it is loaded automatically.

16. Enable the **External standby orchestrator interface** to allow the orchestrator to manage failover operations by recognizing a standby orchestrator for redundancy and resilience, following the steps:

      a. Complete the [External orchestrator interface setup](/docs/dr-automation-powervs?topic=dr-automation-powervs-manage-exter).  
      b. Hover over the **External standby orchestrator interface** button to view the standby orchestrator IP, for example, `IP:xx.x.x.xxx`.  
      c. Use the standby orchestrator IP and add it in the [**Add Node**](/docs/dr-automation-powervs?topic=dr-automation-powervs-nav-pan#ksys-set-tab-detai) section.  
      d. Click the **External standby orchestrator interface** button to enable the interface.  
      e. Click the **Refresh** icon to update the status, enabling the **External standby orchestrator interface button** for use.
17. If any error occurs during deployment, follow on-screen prompts or events to troubleshoot and retry the deployment.

By following this process, you can ensure that your orchestrator is fully equipped to manage disaster recovery operations for your virtual servers.

## Power Edge Router and non Power Edge Router
{: #pow-ed-ro-non-pow-ed-rou}

Power Virtual Server DR Automation supports both Power Edge Router(PER) and non Power Edge Router(PER) workspaces.

### Procedure 
{: #procedure-non-per}

To use a non PER enabled workspace, complete the following manual steps before using them:

1. Create a Cloud connection by attaching all the available subnets that are used for communication from your non PER enabled Power Virtual Server workspace.
2. Verify that the Cloud connection status changes to Active.
3. Attach the Cloud connection to the Transit gateway.
4. Select the **Transit gateway** -> **Add connection** -> Select Direct Link and select the newly created direct link -> click **Add**.

You can now use a non-PER enabled Power Virtual Server workspace by following the steps above. The setup ensures that your workspace is ready for network communication.

## Enable communication via VPC
{: #procedure-ena-ppro-comm}
1. Open [IBM Cloud console](https://cloud.ibm.com).
2. Click **Navigation menu** icon > **Infrastructure** > **Network** > **VPCs**, and select your VPC from the list.
3. Create a **Virtual Server Instance (VSI)** under the **Compute** section.
4. Enable public gateway for the VSI subnet. Click **Navigation menu** icon > **Infrastructure** > **Network** > **Subnets** > Enable **Detached** in Public gateway > Click **Attach** and this enables the public gateway for VPC subnet.
5. Configure the Squid proxy on the VSI by running the following commands:
   ```
   yum -y install squid
   systemctl start squid
   systemctl enable squid

   yum install firewalld
   systemctl start firewalld
   systemctl enable firewalld
   firewall-cmd --add-port=3128/tcp --permanent
   firewall-cmd --reload
   systemctl status firewalld
   ```
6. To verify the squid configuration, run the following command:
    `systemctl status squid`

    An output that is similar to the following example is displayed:
    ```
    ● squid.service - Squid caching proxy
      Loaded: loaded (/usr/lib/systemd/system/squid.service; enabled; preset: disabled)
      Active: active (running) since Mon 2025-07-07 11:19:52 UTC; 2 days ago
    ```

    **Note:** Ensure that Squid configuration is in Active and running state.

7. To verify port number is up and running:
    `sudo netstat -tulnp | grep 3128`


An output that is similar to the following example is displayed:
   ```
   tcp6  0  0 :::3128   :::*   LISTEN    16742/(squid-1)
   ```
 For more information, see Configuring the [Squid proxy server](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/7/html/networking_guide/configuring-the-squid-caching-proxy-server) in the Red Hat documentation.
