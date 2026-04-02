---
copyright:
  years: 2025
lastupdated: "2026-04-02"

subcollection: dr-automation-powervs

keywords: ha, plugin-cli plugin

---

# Installing the {{site.data.keyword.DR_full_notm}} PowerHA AIX CLI plug-in
{: #ha-plun-in}

To install, update, or view the {{site.data.keyword.DR_full_notm}} PowerHA AIX  CLI plug-in, complete the following steps:

1. Install the [IBM Cloud® CLI](https://cloud.ibm.com/docs/cli).

2. Install or update the `power-hadr` plug-in.

    **To install**

    ```bash
    ibmcloud plugin install power-hadr
    ```

    **To update**

    ```bash
    ibmcloud plugin update [PLUGIN_NAME]
    ```

    **To view your installed plug-ins and versions:**

    ```bash
    ibmcloud plugin list
    ```

3. Verify the installed plug-in by running the following command:

    ```bash
    ibmcloud power-hadr
    ```

    The output is as follows:
    
    ```
    ibmcloud power-hadr
    NAME:
         power-hadr - Manage IBM Power Virtual Server High Availability and Disaster Recovery Service
    USAGE:
         ibmcloud power-hadr [command] [options]
    VERSION:
         0.0.4
    COMMANDS:
         pdr, dr            Manage Disaster Recovery Automation Service.
         powerhasm, phasm   Manage PowerHA SystemMirror cluster.
    OPTIONS:
        -h, --help      Show help
        -v, --version   Version of the plug-in.
    Use "ibmcloud power-hadr <command> --help" for more information about a command.
        [user@host cli-plugin]
    ```

4. You can use the CLI commands available for PowerHA AIX.

Refer to the full CLI documentation [{{site.data.keyword.DR_full}} PowerHA AIX CLI](/docs/dr-automation-powervs?topic=dr-automation-powervs-dr-automation-cli-version).
