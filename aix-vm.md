---
copyright:
  years: 2025
lastupdated: "2025-11-04"

subcollection: dr-automation-powervs

keywords: aix

---

# Creating an AIX virtual machine (VM)
{: #aix-virtu}

You can set up one or more Secure Shell (SSH) keys for root login when you create new AIX virtual machines (VM). The keys are loaded into the root's `authorized_keys` file. SSH keys allow you to securely log in to a VM. You must use the available operating system options to create SSH keys. To generate SSH keys on a Linux® or Mac OS system, for example, you can use the standard `ssh-keygen` tool.
{:shortdesc: .shortdesc}

## Creating an AIX VM instance
{: #vm-insta}

You can create an AIX VM instance with a configured SSH key by using the VM Recovery Manager DR CLI or the console. When you use an AIX stock image as your boot volume, the root password is not set. You must connect to the AIX VM and set the root password for the system. Without completing this step, SSH login as root appears as being disabled. If you have public network access to the AIX VM, you can use telnet from a private cloud system and set the root password. For more information, see [IBM AIX V7.3 documentation](https://www.ibm.com/docs/en/aix/7.3).
