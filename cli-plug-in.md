---
copyright:
  years: 2025
lastupdated: "2025-11-26"

subcollection: dr-automation-powervs

keywords: plugin-cli plugin

---

**To install**

>```
>    ibmcloud plugin install power-hadr
>```

> **To update**

>```
>    ibmcloud plugin update
>```

**To view your installed plug-ins and versions:**
>```
>    ibmcloud plugin list
>```

3. Verify the installed plug-in,by running the following command:

```
    ibmcloud plugin list
```

The out put is as following:

```
    ibmcloud power-hadr
    NAME:
    power-hadr - Commands to manage power-hadr.
    USAGE:
    ibmcloud power-hadr [command] [options]
    VERSION:
    0.0.1
    COMMANDS:
    pdr, dr   Manage DrAutomation Service.
    OPTIONS:
    -h, --help      Show help
    -v, --version   Version of the plug-in.
    Use "ibmcloud power-hadr <command> --help" for more information about a command.
    [root@dra-sb dra-cli-plugin]
```

4. You can use the other CLI commands available for {{site.data.keyword.DR_full_notm}}.

Refer to the full CLI documentation [{{site.data.keyword.DR_full}} CLI version 0.0.1](/docs/dr-automation-powervs?topic=dr-automation-powervs-dr-automation-cli-version).

> **Note**: The {{site.data.keyword.DR_full}} CLI plug-in requires a valid IAM token authorization before each use. Use the ibmcloud login command to renew authorization if your token expires.
