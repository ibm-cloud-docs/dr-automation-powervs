---

copyright:
  years: 2025
lastupdated: "2025-11-26"

subcollection: dr-automation-powervs

keywords: MFA, multifactor authentication

---
# Multifactor authentication
{: monitor-multi-ibm}

## Setting up multifactor authentication
{: monitor-multi-auten}

You can enable Multi-Factor Authentication (MFA) in {{site.data.keyword.DR_full}} to enhance access security by requiring users to enter their password first, followed by a one-time passcode (OTP), when logging in to the orchestrator GUI.

MFA is configured by integrating the orchestrator with **IBM Security Verify**. During deployment, you provide the **Client ID**, **Client Secret**, and **Tenant Name** that correspond to your IBM Security Verify tenant. The deployment process uses these values to register the orchestrator and the **root** user with IBM Security Verify. When MFA is enabled during deployment, the root user is prompted for an OTP during the first login and in all subsequent logins while MFA remains enabled.

If multiple orchestrators are deployed using the same IBM Security Verify tenant, the service automatically detects and **reuses** the existing registration. If an orchestrator is removed and it is the **last** one associated with that tenant, the registration is also removed. This ensures that tenant-based billing and registrations remain aligned with your usage. The MFA status for a deployed orchestrator is displayed in the **Orchestrator Details** page and all MFA-related events are recorded in the **Events** log for audit tracking.

Multi-Factor Authentication (MFA) in the Orchestrator requires internet connectivity. Ensure that your Power Virtual Server workspace has access to the external network. If you are using a proxy for outbound communication, provide the proxy IP and port in the proxy details. During deployment, the proxy settings are automatically exported to the Orchestrator.


## Prerequisites
{: monitor-pre-ibm}

Before enabling MFA, you must configure a tenant in [**IBM Security Verify**](https://www.ibm.com/account/reg/us-en/signup?formid=urx-30041&_ga=2.41335909.671467744.1669106438-1806696627.1657020197) and obtain the credentials needed for integration.

1. Register or sign in to the [**IBM Security Verify**](https://www.ibm.com/account/reg/us-en/signup?formid=urx-30041&_ga=2.41335909.671467744.1669106438-1806696627.1657020197) portal.
2. Create and configure a tenant.
3. From the portal navigation, select **Security > API access**.
4. Copy the **Client ID** and **Client Secret** from the **API Credentials** section.
5. Note your **Tenant Name**.

These values are entered during [Deploying the orchestrator](/docs/dr-automation-powervs?topic=dr-automation-powervs-idep-the-orch) or when adding MFA to an existing environment.

## Enabling MFA during orchestrator deployment (root user)
{: monitor-met-ibm}

You can enable MFA during the deployment of the orchestrator, which applies immediately to the **root** user.

1. In the deployment configuration, expand **Advanced Settings**.
2. Select **Enable MFA**.
3. Enter the **Client ID**, **Client Secret**, and **Tenant Name** obtained from IBM Security Verify.
4. Complete the remaining deployment configurations and deploy the orchestrator.

After deployment, when the root user logs in to the External Orchestrator GUI, the login screen prompts for the root password and post authentication of root password, generates an OTP. The OTP is delivered to the IBM Cloud registered email. The orchestrator is registered in IBM Security Verify as part of the deployment and remains registered until the last deployment is deprovisioned.

You can manage user accounts, roles, and permissions through the User Role Management page. For more information, see [User role management](/docs/dr-automation-powervs?topic=dr-automation-powervs-user-ro-mang).

> **Note**: If incorrect values are provided for the client ID, client secret, or tenant name, the deployment process still completes successfully, but MFA will not be enabled.
