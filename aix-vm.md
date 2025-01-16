---
copyright:
  years: 2025
lastupdated: "2025-01-16"

subcollection: dr-automation

keywords: aix

---

# Creating an AIX virtual machine (VM) with SSH keys for root login
{: #aix-virtu}

You can set up one or more Secure Shell (SSH) keys for root login when you create new AIX virtual machines (VM). The keys are loaded into the root's `authorized_keys` file. SSH keys allow you to securely log in to a VM. You must use the available operating system options to create SSH keys. To generate SSH keys on a Linux® or Mac OS system, for example, you can use the standard `ssh-keygen` tool.
{:shortdesc: .shortdesc}

## Generating an SSH key
{: #gen-ssh}

In this example, the user created a public key on a Linux-based IBM Cloud compute instance by using the `ssh-keygen` tool:


## Creating an AIX VM instance
{: #vm-insta}

You can create an AIX VM instance with a configured SSH key by using the VM Recovery Manager DR CLI or the console. When you use an AIX stock image as your boot volume, the root password is not set. You must connect to the AIX VM and set the root password for the system. Without completing this step, SSH login as root appears as being disabled. If you have public network access to the AIX VM, you can use telnet from a private cloud system and set the root password. For more information, see [IBM AIX V7.3 documentation](https://www.ibm.com/docs/en/aix/7.3).

## Creating an AIX VM with a configured SSH key using UI
{: #ssh-key-ui}

You must [generate a public SSH key](#) before you can create an AIX VM with a configured SSH key.

1. Ensure that you have the necessary account permissions and device access. Only the account owner, or a user with the **Manage Users** classic infrastructure permission, can adjust the permissions. For more information, see [Classic infrastructure permissions](#) and [Managing device access](#).

2. Click **Virtual server instances** from the left navigation in the Power Virtual Server user interface.

3. Click **Create instance**.

4. In the **Virtual servers** section, select **Add SSH Keys**.

5. Enter a **Key name** and your previously generated **Public key**.

6. Click **Add SSH key** to add the SSH key.

7. Complete the rest of the fields to successfully create a new instance with a configured SSH key.


## Creating an AIX VM with a configured SSH key using CLI
{: #using-cli}

You can create a new VM with the public key by using the following command (replacing the options with your own)
