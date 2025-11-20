---

copyright:
  years: 2025
lastupdated: "2025-11-20"

subcollection: dr-automation-powervs

keywords: MFA, multifactor authentication

---
# Setting up multifactor authentication
{: monitor met-ibm}

You can enable Multi-Factor Authentication (MFA) in {{site.data.keyword.DR_full}} to enhance access security by requiring users to enter their password first, followed by a one-time passcode (OTP), when logging in to the DR automation GUI.

MFA is configured by integrating the orchestrator with **IBM Security Verify**. During deployment, you provide the **Client ID**, **Client Secret**, and **Tenant Name** that correspond to your IBM Security Verify tenant. The deployment process uses these values to register the orchestrator and the **root** user with IBM Security Verify. When MFA is enabled during deployment, the root user is prompted for an OTP during the first login and in all subsequent logins while MFA remains enabled.

If multiple orchestrators are deployed using the same IBM Security Verify tenant, the service automatically detects and **reuses** the existing registration. If an orchestrator is removed and it is the **last** one associated with that tenant, the registration is also removed. This ensures that tenant-based billing and registrations remain aligned with your usage. The MFA status for a deployed orchestrator is displayed in the **Orchestrator Details** page and all MFA-related events are recorded in the **Events** log for audit tracking.


## Prerequisites
{: monitor met-ibm}

Before enabling MFA, you must configure a tenant in **IBM Security Verify** and obtain the credentials needed for integration.

1. Register or sign in to the **IBM Security Verify** portal.
2. Create and configure a tenant.
3. From the portal navigation, select **Security > API access**.
4. Copy the **Client ID** and **Client Secret** from the **API Credentials** section.
5. Note your **Tenant Name**.

These values are entered during orchestrator deployment or when adding MFA to an existing environment.


## Enabling MFA during orchestrator deployment (root user)
{: monitor met-ibm}

You can enable MFA during the deployment of the orchestrator, which applies immediately to the **root** user.

1. In the deployment configuration, expand **Advanced Settings**.
2. Select **Enable MFA**.
3. Enter the **Client ID**, **Client Secret**, and **Tenant Name** obtained from IBM Security Verify.
4. Complete the remaining deployment configurations and deploy the orchestrator.

After deployment, when the root user logs in to the GUI, the login screen prompts for both the root password and an OTP. The OTP is delivered to the root user’s registered email. The orchestrator is registered in IBM Security Verify as part of the deployment and remains registered unless this is the last orchestrator instance associated with that tenant.

---





