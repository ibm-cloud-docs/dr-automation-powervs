---
copyright:
  years: 2025
lastupdated: "2025-07-08"

subcollection: dr-automation

keywords: manage vm

---

# Managing virtual servers
{: #manage-vm-ser}



To set up and manage additional virtual server instances,you can use either DR Automation management UI or access the external orchestrator interface to add and manage advanced configuration for enabling disaster recovery.
   > **Note**: Currently IBM Power Virtual Server Private Cloud officially supports Red Hat Enterprise Linux (RHEL), IBM i, and IBM AIX® operating systems for creating virtual servers.
## Add virtual servers
{: #manage-vm-ser-added}

1. Navigate to the **Manage Virtual Servers** table.
   > **Note**: DR Automation supports all virtual server instances as Managed Virtual Servers that are created through IBM Power Virtual Server. To learn more about all the supported Managed Virtual Server instances, click [IBM Power Virtual Server documentation](https://cloud.ibm.com/docs/power-iaas){: external}.
2. Click **Add Virtual Server** button.
3. You are redirected to the external orchestrator interface (UI),The orchestrator UI is launched at
https://`<Orchestrator IP>`:3000/login.
   > **Note**: The `<Orchestrator IP>` is the system on which the orchestrator UI is installed and it is loaded automatically.
4. In the external orchestrator interface, follow the guided steps to configure and add **virtual servers** to your disaster recovery setup.
5. After the servers are successfully added, the servers are displayed in the list under **Managed Virtual Servers**.

Efficient management of virtual servers through the {{site.data.keyword.DR_short}} interface, coupled with the external orchestrator, ensures that your disaster recovery environment remains scalable and resilient. This seamless process provides confidence that your critical systems will be protected in the face of potential failures, maintaining business continuity.

For more information about **External Orchestrator Interface (UI)**, see [IBM VM Recovery Manager DR for Power Systems](https://www.ibm.com/docs/en/vmrmdr).
