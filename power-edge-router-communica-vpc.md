---

copyright:
  years: 2025
lastupdated: "2026-04-29"

subcollection: dr-automation-powervs

keywords: non Power Edge Router, power edge, enable communication vpc

---

# PER and non-PER workspace networking
{: #supp-power-edge}

Explains how {{site.data.keyword.DR_full}} supports Power Edge Router (PER) and non-PER workspaces, including the required network setup and proxy configuration to enable communication.

## Power edge router and non power edge router
{: #pow-ed-ro-non-pow-ed-rou}



Power Edge Router (PER) and non-PER workspaces determine how network connectivity is established for your Power Virtual Server environment.

### Procedure 
{: #procedure-non-per}

To use a non-PER workspace, complete the following steps to enable network communication:

1. Create a Cloud connection by attaching all the available subnets that are used for communication from your non PER enabled Power Virtual Server workspace.
2. Verify that the Cloud connection status changes to Established.
3. Attach the Cloud connection to the Transit gateway.
4. Select **Transit gateway** -> **Add connection** -> Select Direct Link and, select the newly created direct link -> click **Add**.

You can now use a non-PER enabled Power Virtual Server workspace by following the preceding steps. The setup ensures that your workspace is ready for network communication.

## Enable communication via VPC
{: #procedure-ena-ppro-comm}

Configure a VPC and proxy to enable outbound communication from a non-PER workspace.

### Procedure 
{: #procedure-commun-cpv}

1. Open [IBM Cloud console](https://cloud.ibm.com).
2. Click **Navigation menu** icon > **Infrastructure** > **Network** > **VPCs**, and select your VPC from the list.
3. Create a **Virtual Server Instance (VSI)** under the **Compute** section.
4. Enable a public gateway for the VSI subnet. Click **Navigation menu** icon > **Infrastructure** > **Network** > **Subnets** > Enable **Detached** in Public gateway > Click **Attach** and this enables the public gateway for VPC subnet.
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

    **Note:** Ensure that the Squid configuration is in an Active and running state.

7. To verify that the port number is up and running:
    `sudo netstat -tulnp | grep 3128`


An output that is similar to the following example is displayed:
   ```
   tcp6  0  0 :::3128   :::*   LISTEN    16742/(squid-1)
   ```
 For more information, see Configuring the [Squid proxy server](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/7/html/networking_guide/configuring-the-squid-caching-proxy-server) in the Red Hat documentation.

  > **Note (PowerHA only):** Ensure that the Squid proxy IP is exported on the PowerHA node to enable connectivity for downloading the PowerHA filesets:  
> `http_proxy=http://<squid_proxy_ip>:<port>`  
> `https_proxy=http://<squid_proxy_ip>:<port>`  
>
> Example:  
> `http_proxy=http://10.30.40.4:3128`  
> `https_proxy=http://10.30.40.4:3128`  
>
> If these variables are not set, the PowerHA agent cannot download the filesets and fails with connectivity errors.
