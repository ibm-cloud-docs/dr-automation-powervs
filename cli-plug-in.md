---
copyright:
  years: 2025
lastupdated: "2025-12-03"

subcollection: dr-automation-powervs

keywords: plugin-cli plugin

---

# Installing the {{site.data.keyword.DR_full_notm}} CLI plug-in
{: #plun-in}

To install, update, or view the {{site.data.keyword.DR_full_notm}} CLI plug-in, complete the following steps:

1. Install the [IBM Cloud® CLI](https://cloud.ibm.com/docs/cli).

2. Install or update the `power-hadr` plug-in.

    **To install**

    ```bash
    ibmcloud plugin install power-hadr
    ```

    **To update**

    ```bash
    ibmcloud plugin update
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
    NAME:  power-hadr - Commands to manage power-hadr.
    USAGE: ibmcloud power-hadr [command] [options]
    VERSION: 0.0.1
    COMMANDS: pdr, dr   Manage DrAutomation Service.
    OPTIONS:  -h, --help      Show help
              -v, --version   Version of the plug-in.
    Use "ibmcloud power-hadr <command> --help" for more information about a command.
    [root@dra-sb dra-cli-plugin]
    ```

4. You can use the CLI commands available for {{site.data.keyword.DR_full_notm}}.

Refer to the full CLI documentation [{{site.data.keyword.DR_full}} CLI version 0.0.1](/docs/dr-automation-powervs?topic=dr-automation-powervs-dr-automation-cli-version).

> **Note**: The {{site.data
