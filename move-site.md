---

copyright:
  years: 2025
lastupdated: "2025-01-16"

subcollection: dr-automation

keywords: move

---
# Move site operation
{: #smove-siter}

Move site is a critical functionality designed to manage the relocation of virtual machines (VMs) and services from one site to another. This operation encompasses two primary actions: Planned Move and Unplanned Move.
{:shortdesc: .shortdesc}

To perform a Planned Move or Unplanned Move of the site, follow these steps:

1. Click on **Site** in the navigation panel.
2. Navigate to **Move Site**.
3. Choose either **Planned Move** or **Unplanned Move**.

  >  **Note:**
  > - A Planned Move involves shutting down the VM on the currently active site and starting the backup VM on the target site. This process will result in a temporary disruption at the active site.
  > - An Unplanned Move is executed when the currently active site is compromised or non-operational. During an Unplanned Move, the KSYS system will attempt to shut down the VM on the active site before initiating recovery on the backup site.

4. Choose **Yes** or **No**.

> **Note:** This step includes a force-move option. If an unplanned recovery is necessary, you can select this option to forcibly transfer the VMs from the active site to the backup site.

5. Specify the **Target Site** to which the VMs will be moved.
6. Click **Move Site** to initiate the relocation process.
