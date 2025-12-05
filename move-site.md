---

copyright:
  years: 2025
lastupdated: "2025-11-26"

subcollection: dr-automation-powervs

keywords: move

---
# Move site operation
{: #smove-siter}

Move site is a critical functionality that is designed to manage the relocation of virtual machines (VMs) and services from one site to another. This operation encompasses two primary actions: Planned Move and Unplanned Move.
{:shortdesc: .shortdesc}

To perform a Planned Move or Unplanned Move of the site, follow these steps:

## Procedure
{: #smove-pro}

1. Click **Site** in the navigation panel.
2. Navigate to **Move Site**.
3. Choose either **Planned Move** or **Unplanned Move**.

   > **Note:**
   >
   > - A **Planned Move** shuts down the VM on the currently active site and starts the backup VM on the target site. This results in a temporary disruption at the active site.
   > - An **Unplanned Move** is used when the active site is compromised or non-operational. KSYS attempts to shut down the VM on the active site before initiating recovery on the backup site.

4. Select **Yes** or **No**.

   > **Note:** This step includes a force-move option. If an unplanned recovery is necessary, you can use this option to forcibly transfer the VMs from the active site to the backup site.

5. Specify the **Target Site** where the VMs must be moved.
6. Click **Move Site** to initiate the relocation process.
