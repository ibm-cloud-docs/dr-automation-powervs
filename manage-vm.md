---
copyright:
  years: 2025
lastupdated: "2025-02-25"

subcollection: dr-automation

keywords: manage vm

---

# Managing virtual servers
{: #manage-vm-ser}

Manage Virtual Servers within the {{site.data.keyword.DR_full}} enables administrators to monitor and control the virtual server instances that are part of the disaster recovery environment. Through this interface, users can manage existing virtual servers, check their current status, and perform actions such as adding or removing servers to maintain optimal DR operations. This tool ensures that all servers involved in the DR plan are properly orchestrated and functional, safeguarding business continuity in the event of failures.

To set up additional virtual server instances and manage them within the {{site.data.keyword.DR_full_notm}} framework, users can either add virtual servers directly or access the external orchestrator interface for advanced configurations.

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

For more information about **external Orchestrator Interface (UI)**, see [IBM VM Recovery Manager DR for Power Systems](https://www.ibm.com/docs/en/vmrmdr).
