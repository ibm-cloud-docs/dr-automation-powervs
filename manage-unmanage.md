# Managing and Unmanaging VMs

## Manage VM

You can view and manage VMs using the VM Recovery Manager DR (GUI). Managing a VM allows it to be included in disaster recovery operations and monitored effectively.


To manage the VMs, complete the following steps:

1. In the navigation pane of the VM Recovery Manager DR, click **Site > WorkSpace > Managed this VM**.
2. Select the VM.
3. Click **Manage this VM**.

   You are redirected to the Managed VM tab, where you can view details such as:
   - VM Name
   - WorkGroup
   - Source Workspace
   - Target Workspace

   **Note:** The WorkGroup name is auto-generated based on the VM name. You can change it as per your requirements.

---

## Unmanage VM

You can view and unmanage VMs using the VM Recovery Manager DR (GUI). Unmanaging a VM removes it from disaster recovery operations and monitoring.

To unmanage the VMs, complete the following steps:

1. In the navigation pane of the VM Recovery Manager DR, click **Site > WorkSpace > Unmanaged this VM**.
2. Select the VM.
3. Click **Unmanage this VM**.

   After this operation, the WorkGroup is removed from the list.

   **Note:** 
   - Each WorkGroup is associated with only one VM.  
   - You can unmanage a VM even if it has not been managed previously.
