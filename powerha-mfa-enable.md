---
copyright:
  years: 2025
lastupdated: "2026-04-24"

subcollection: dr-automation-powervs

keywords: private pod, client location

---


# Enabling MFA for PowerHA Cloud (AIX private nodes)
{: #mfa-enablement-powerha}

## Overview
{: #mfa-overview}

After deploying the PowerHA node and completing the agent and dependency installation, you can access the PowerHA GUI hosted on the node. From this GUI, you can configure extra security feature such as Multi-Factor Authentication (MFA).

MFA provides an extra layer of security for users accessing the PowerHA GUI. In PowerHA Cloud, MFA is configured through the GUI hosted on AIX nodes.

For private cloud deployments, extra configuration (such as proxy enablement) is required to allow communication with the identity provider.

> **Note:** MFA configuration is performed on the PowerHA GUI hosted on the node, not from the IBM Cloud UI.

## Before you begin
{: #mfa-prerequisites}


Ensure that the following prerequisites are met:

- Root access to the AIX private node hosting the PowerHA on-premises GUI is required.
- An [IBM Security Verify](https://www.ibm.com/account/reg/us-en/signup?formid=urx-30041&_ga=2.41335909.671467744.1669106438-1806696627.1657020197) tenant and application must be configured, with the following details:
  - Client ID
  - Client secret
- Outbound connectivity to the required identity provider endpoints enabled through a configured internet proxy.

> **Note:**
> Proxy configuration is mandatory for private nodes to enable MFA functions.

  ```
  https://<node-ip>:<port>/login
  ```



> **Important:**
> The PowerHA GUI is available after installing the agent and required dependencies on the node.

## Step 1: Configure proxy on private nodes
{: #mfa-step1-proxy}

For private nodes, outbound connectivity is required to communicate with the identity provider. For more information, see [Enabling proxy](https://cloud.ibm.com/docs/powervs-vpc)

```bash
export https_proxy="10.30.40.4:3128"
export http_proxy="10.30.40.4:3128"
```

> **Note:**
> - Proxy configuration is mandatory for private nodes.
> - For public nodes, MFA can work without proxy configuration.


## Step 2: Create a non-root user
{: #mfa-step2-user}

MFA applies only to non-root users.

```bash
cd /home
mkdir test
useradd test
passwd test
```

## Step 3: Configure sudo (optional)
{: #mfa-step3-sudo}

If your workflow requires elevated privileges for GUI operations or supporting commands, configure `sudo` based on your organization's policy.

To safely edit the sudoers file, run:

```bash
visudo
```

Example:

```bash
User_Alias POWERHA_GUI_USERS = ajay, sumantra

```
The following is the output for the preceding example:

```bash
# lspv
hdisk0   00cde1b7528d66f2   None
hdisk1   00cde1b7528d6732   None
hdisk2   00cde1b7528d6771   None
hdisk3   00cde1b7528d67c1   None
hdisk4   00cde1b7528d6805   None
hdisk5   00cde1b7527593ca   rootvg   active

# hostname
rlrm4p32.phalab.local
# visudo
```

After opening the `sudoers` file, add or update user aliases as needed. For example:

```bash
User_Alias POWERHA_GUI_USERS = <user1>, <user2>  # for example, ajay, sumantra
```

> **Note:** This step is required only if your environment uses `sudo` to manage user access for PowerHA operations.

```bash
# sudoers file.
# This file MUST be edited with the 'visudo' command as root.
# Failure to use 'visudo' may result in syntax or file permission errors
# that prevent sudo from running.
# See the sudoers man page for the details on how to write a sudoers file.
# Host alias specification
# User alias specification
User_Alias POWERHA_GUI_USERS = prudhvi, balte, shivam, mad
# Cmnd alias specification
# Defaults specification
# Runas alias specification
# User privilege specification
root    ALL=(ALL) ALL
# Uncomment to allow people in group wheel to run all commands
# %wheel    ALL=(ALL) ALL
# Same thing without a password
# %wheel    ALL=(ALL) NOPASSWD: ALL
# Samples
# Users ALL=/sbin/mount /cdrom,/sbin/umount /cdrom
# Users localhost=/sbin/shutdown -h now
User_Alias POWERHA_GUI_USERS = dummy, demo, prudhvi, mad
Cmnd_Alias POWERHA_GUI_CMDS = \
/usr/es/sbin/cluster/utilities/clmgr -v query nodes, \
/usr/es/sbin/cluster/utilities/clmgr list hosts TYPE=$TYPE, \
/usr/es/sbin/cluster/utilities/clmgr -g SMUI list physical_volume NODES=$NODES, \
/usr/es/sbin/cluster/utilities/clmgr query cluster, \
/usr/es/sbin/cluster/utilities/clmgr -v query physical_volume NODES=$NODES TYPE=all, \
/usr/es/sbin/cluster/utilities/clmgr -t $ACTIVITY ID add cluster $NAME NODES=$NODES TYPE=$TYPE REPOSITORIES=$DISKS, \
/usr/es/sbin/cluster/utilities/clmgr -t $ACTIVITY ID remove cluster $NAME NODES=$NODES TYPE=$TYPE
```

## Step 4: Enable MFA in the UI server
{: #mfa-step4-enable}

To enable MFA support in the PowerHA GUI, update the UI server configuration on the private node.

### Update server configuration
{: #mfa-server-config}

Open the `server.json` file:

```
/usr/es/sbin/cluster/ui/server/node_modules/smui_server/lib/configuration/default/server.json
```

Add the following configuration:

```json
"mfaConfiguration": {
  "proxy": "http://10.30.40.4:3128",
  "client_id": "<client_id>",
  "client_secret": "<client_secret>",
  "tenant": "tenantname.verify.ibm.com"
}
```
Replace the placeholder values with your actual configuration.

> **Important:**
> - Proxy configuration is required for private nodes.
> - Without this configuration, the MFA option is not available in the GUI.

### Restart the UI server
{: #mfa-restart-ui}

Restart the PowerHA UI server to apply the updated configuration:

```bash
stopsrc -s phauiserver
startsrc -s phauiserver
```

After the restart, the **Enable MFA for this user** option is available when creating a user in the GUI.

## Step 5: Enable MFA for a user
{: #mfa-step5-user}

1. Open the PowerHA GUI in a browser:
   ```
   https://<node-ip>:<port>
   ```
2. Log in using root or administrator credentials.
3. From the upper-right menu, select **Users**.
4. Click **Add user**.
5. Enter the required user details and select **Enable MFA for this user**.
6. Click **Continue**.
7. Assign the required role (for example, `ha_root`).
8. Click **Submit** to create the user.

> **Note:** The **Enable MFA for this user** checkbox is visible only after updating `server.json` and restarting the UI server.

After successful creation, the user is listed with MFA enabled.


## Step 6: MFA enrollment (non-root user)
{: #mfa-step6-enrollment}

1. MFA enrollment must be performed by a non-root user. Use the account that you created in [Step 2](#mfa-step2-user).

2. Log in to the PowerHA GUI using the non-root user credentials. <stagging>comment :which credentials</stagging>

If MFA is enabled for the user, the system prompts for MFA enrollment instead of displaying the dashboard.


## Step 7: Configure authentication methods
{: #mfa-step7-methods}

After login, select an authentication method to begin MFA setup.

Available authentication methods depend on tenant configuration:

- Email OTP  
- Mobile OTP  
- OTP through call  

### Select authentication method
{: #mfa-select-verify}

1. Select an authentication method.
2. Click **Next** to proceed with verification.
3. Enter the OTP received.
4. Click **Verify OTP**.

> **Note:** If you are unable to complete verification by using a selected method, you can choose an alternative authentication method.

After successful verification, a confirmation message is displayed.


### TOTP authentication
{: #mfa-totp-flow}

1. click Users on the profile page.
2. select the user and click **view profile**.
3. Select **TOTP Registration**.
4. Generate or view the QR code.
5. Scan the QR code by using:
   - Google Authenticator, or  
   - IBM Verify app  
6. Enter the generated OTP.
7. Click **Verify**.

After verification, the TOTP method is marked as active.

### Signature authentication
{: #mfa-signature-flow}

1. Select **Verify through Signature**.
2. Click **Next**.

3. Select one of the following:
   - **User Approval**
   - **Fingerprint/Face**

4. Complete authentication by using the IBM Verify mobile app.

After successful verification, the method is enabled.


## Validation
{: #mfa-validation}

Verify that MFA is enabled and functioning correctly:

- The **Enable MFA for this user** option is visible in the GUI after updating `server.json` and restarting the UI server.
- Non-root user login prompts for MFA enrollment.
- Selected authentication methods show as **Verified** or **Active**.
- Users can sign out and sign back in successfully using MFA.

## Troubleshooting
{: #mfa-troubleshooting}

- Ensure that the proxy is configured and reachable.
- Verify tenant, client ID, and client secret values.
- Ensure that dependencies are installed and the GUI is accessible.
- Restart UI server after configuration changes.
