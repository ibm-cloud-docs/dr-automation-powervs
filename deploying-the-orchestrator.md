---
copyright:
  years: 2025
lastupdated: "2025-07-11"

subcollection: dr-automation

keywords: deploy the orch

---

# Deploying the orchestrator
{: #idep-the-orch}

After creating the resource, deploying the orchestrator for DR automation is essential to can ensure that your Power Virtual Server environment is protected against disaster events. The orchestrator coordinates disaster recovery operations, including replication, failover, and failback of virtual machines. This screen displays high availability (HA) settings, authentication keys and resource allocation. Once deployed, the orchestrator can manage multiple virtual servers and help ensure continuous availability.
{:shortdesc: .shortdesc}

 >**Note**: 
>- The orchestrator VM is created with the default configuration of 0.5 CPU units and 4 GB memory.
>- This configuration is suitable for managing 20 PowerVS instances.
>- If you need to manage more than 20 Managed VMs, it is recommended to increase the configuration to 1 CPU unit and 6 GB of memory.

## Deploying the orchestrator for disaster recovery
{: #dep-the-orch-dis-re}

### Procedure 
{: #procedure}

To deploy the orchestrator with the necessary configurations to meet your disaster recovery requirements,
follow the steps:

1. After completing the **Create** resource step, you are redirected to the **Manage** tab to proceed with the deployment.

2. In the configure primary orchestrator section, enter the **DR Orchestrator name**.

3. Set a password in the **DR Orchestrator password** field and re-enter the password in **Confirm DR orchestrator password** section to secure access to the external orchestrator interface.
   > **Note**: This password is set for the Orchestrator VM, and you can use it to login to the Orchestrator VM UI.

4. Provide a valid **IBM Cloud API key**.
   > **Note**: Enter your API key, which is required to access various services described in [Access role requirements for Power Virtual Server DR Automation](/docs/dr-automation-powervs?topic=dr-automation-powervs-iam-manage#ser-acc-role-dr-auto). Can ensure that the API key has the necessary permissions for proper functions.

5. In the **DR location** field, select the target region for deploying the orchestrator VM.

6. Select **Schematic workspace** or **Custom VPC** to manually configure the network settings for the orchestrator deployment.

   - Select the **Schematic workspace** and follow the steps:

      1. Select an appropriate workspace for the orchestrator in the **DR Schematic workspace (VPC)** field.
      2. Create a [VPC landing zone](https://cloud.ibm.com/catalog/architecture/deploy-arch-ibm-pvs-inf-2dd486c7-b317-4aaa-907b-42671485ad96-global/readme/terraform/terraform/e104e91d-d4a8-44fa-a341-eebf735d9635-global) if required, to define the Power Virtual Server workspace where the primary orchestrator is deployed.
         > **Note**: The schematic ID is available if the VPC is created by using the VPC Landing Zone for the PowerVS option from the catalog.

   - Select **Custom VPC** and follow the steps:

      1. To go ahead with the custom VPC you will have to finish the following pre-req:

         - Need VPC,  you can create a new [VPC](https://cloud.ibm.com/docs/vpc?topic=vpc-getting-started) or use the existing one.
         - Once VPC is available, configure your VPC to [enable the proxy communication](/docs/dr-automation-powervs?topic=dr-automation-powervs-idep-the-orch#procedure-ena-ppro-comm).
         - Use the existing transit gateway or you can create a new [Transit gatway](https://cloud.ibm.com/docs/transit-gateway?topic=transit-gateway-getting-started). To attach  Transit gateway to a VPC in IBM Cloud. Navigate to **Infrastructure** > **Network** > **Transit Gateway**. Select your transit gateway, and on the **Add connection** page, select the VPC under **Network connection**, choose the **Region**, select the appropriate **Connection reach**, **Select the VPC** from the available connection, and click **Add**.
         -  Once you complete all the pre-req you are ready to use the custom VPC.

      2. Choose the **Transit Gateway** from the dropdown.
      3. Select the VPC from the dropdown.
      4. Enter the Proxy details in `proxyIP:portno` format to enable secure communication between the Orchestrator and external IBM Cloud services. Follow the steps to find the Proxy IP of the VSI:
         - Log in to the [IBM Cloud console](https://cloud.ibm.com).
         - Click **Infrastructure** > **Virtual server instances**.
         - Select the VSI from the list (for example, `test-vsi-test`).
         - Click the VSI name to open its details page.
         - Select the **Networking** tab.
         - Locate the **Reserved IP** in the network attachments section, by default squid uses this reserved IP for the configuration.
         - If the VSI has multiple IPs and you configured `squid.conf` with different IP, that is in `/etc/squid/squid.conf` with the following entry:

            > `http_port <IP>:3128`

         The IP is used as a proxy IP in squid configuration.
      
7. Select the **DR Power Virtual Server workspace** that is listed based on the selected **DR location** and **DR Schematics workspace**. Accordingly, to change the DR Power Virtual Server workspace, update the DR location and DR Schematics workspace.

8. Under **Public SSH Key**, enable the **Use a secret** radio button to use a secret from Secrets Manager. Click **Select from Secrets Manager** and select **Service Instances**, **Secret Groups**, and **Secrets**.

9. Select the SSH key from **SSH key name**.

10. (Optional) Modify the **Advanced Settings** to configure the Storage tier and Machine type based on the **Deploy Orchestrator with HA** selection.

11. In **Configure standby orchestrator (for HA)**, enter the **Standby orchestrator name** and select a **Standby Power Virtual Server workspace** to define the Power Virtual Server workspace in which the standby orchestrator is deployed, when HA is enabled during provision. These settings enable the orchestrator to provide continuous recovery capabilities if the primary site fails.

12. After verifying all settings, click **Deploy orchestrator** to start the deployment process, which creates the orchestrator VMs.

13. **Finish** button is enabled Once the orchestrator VM is deployed.

14. Configure and manage the Power Virtual Server instances through the **External orchestrator interface** for disaster recovery.

  >**Note**: The orchestrator interface (UI) is launched at https://`<Orchestrator IP>`:3000/login. The `<Orchestrator IP>` is the system on which the orchestrator UI is installed and it is loaded automatically.

15. Enable the **External standby orchestrator interface** to allow the orchestrator to manage failover operations by recognizing a standby orchestrator for redundancy and resilience, following the steps:

      a. Complete the [External orchestrator interface setup](/docs/dr-automation-powervs?topic=dr-automation-powervs-manage-exter).  
      b. Hover over the **External standby orchestrator interface** button to view the standby orchestrator IP, for example, `IP:xx.x.x.xxx`.  
      c. Use the standby orchestrator IP and add it in the [**Add Node**](/docs/dr-automation-powervs?topic=dr-automation-powervs-nav-pan#ksys-set-tab-detai) section.  
      d. Click the **External standby orchestrator interface** button to enable the interface.  
      e. Click the **Refresh** icon to update the status, enabling the **External standby orchestrator interface button** for use.
16. If any error occurs during deployment, follow on-screen prompts to troubleshoot and retry the deployment.

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
4. Select the Transit gateway **->** Add connection **->** Select Direct Link and select the newly created direct link **->** click Add.

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
6. To verify the squid configuration , run the following command:

 `systemctl status squid`

An output that is similar to the following example is displayed:
   ```
   ● squid.service - Squid caching proxy
   Loaded: loaded (/usr/lib/systemd/system/squid.service; enabled; preset: disabled)
   Active: active (running) since Mon 2025-07-07 11:19:52 UTC; 2 days ago
   ```
**Note**: Ensure that Squid configuration is in Active and running  state.

7. To verify port number is up and running:
 
 `sudo netstat -tulnp | grep 3128`

An output that is similar to the following example is displayed:

   ```
   tcp6  0  0 :::3128   :::*   LISTEN    16742/(squid-1)
   ```
 For more information, see Configuring the [Squid proxy server](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/7/html/networking_guide/configuring-the-squid-caching-proxy-server) in the Red Hat documentation.
