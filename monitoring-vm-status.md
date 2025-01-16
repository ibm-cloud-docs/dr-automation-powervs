---
copyright:
  years: 2025
lastupdated: "2025-01-16"

subcollection: dr-automation

keywords: monitor status

---

# Monitoring vm status
{: #moni-vm-stat}

When creating one or multiple VMs in **DR Automation for Power Virtual Server** (PowerVS), the process includes various stages indicating the configuration, provisioning, and status of the virtual machines. Each status provides insights into the progress and highlights any potential issues that may arise during the VM creation process.
{:shortdesc: .shortdesc}

By following the outlined statuses below, you can effectively monitor the progress of your VM creation and ensure it aligns with your deployment goals.

## Statuses for creating a single VM
{: #moni-vm-stat-creat}

- **Configure Status**  
  *The service instance is in the configuration phase.*  
  **Status**: `configure`  
  **Details**: Configuring the instance with the required settings.

- **Downloading Orchestrator Image**  
  *The orchestrator image is being downloaded.*  
  **Status**: `downloading-orchestrator-image`  
  **Details**: Preparing the orchestrator by downloading the necessary image.

- **Orchestrator VM Creation In Progress**  
  *The orchestrator VM is being created.*  
  **Status**: `orchestrator-VM-creation-in-progress`  
  **Details**: Setting up the orchestrator virtual machine.

- **VM Build Status**  
  *The orchestrator VM is being built.*  
  **Status**: `orchestrator-VM-creation-in-building`  
  **Details**: Constructing the orchestrator VM with the necessary resources.

- **VM Active Status**  
  *The service instance is being finalized.*  
  **Status**: `orchestrator-VM-creation-in-active`  
  **Details**: The orchestrator VM is active and the service is nearly complete.

- **Provision Complete**  
  *The service instance has been successfully created.*  
  **Status**: `active`  
  **Details**: The VM is now ready for use.

## Statuses for creating multiple VMs
{: #moni-vm-stat-sing}

- **Configure Status**  
  *The service instance is in the configuration phase.*  
  **Status**: `configure`  
  **Details**: Configuring the instance with the required settings.

- **Provision In Progress**  
  *The instance provisioning is in progress.*  
  **Status**: `provision-in-progress`  
  **Details**: The system is provisioning the virtual machines.

- **Downloading Orchestrator Image**  
  *The orchestrator image is being downloaded.*  
  **Status**: `downloading-orchestrator-image`  
  **Details**: Preparing the orchestrator by downloading the image.

- **Orchestrator VM Creation In Progress**  
  *The orchestrator VM is being created.*  
  **Status**: `orchestrator-VM-creation-in-progress`  
  **Details**: Setting up the orchestrator VM.

- **VM Build Status**  
  *The orchestrator VM is being built.*  
  **Status**: `orchestrator-VM-creation-in-building`  
  **Details**: Constructing the orchestrator VM.

- **VM Active Status**  
  *The service instance is being finalized.*  
  **Status**: `orchestrator-VM-creation-in-active`  
  **Details**: The orchestrator VM is active and the service is nearly complete.

- **Provision Complete**  
  *The service instance has been successfully created.*  
  **Status**: `active`  
  **Details**: The multiple VMs are now ready for use.

## Failure status
{: #moni-vm-stat-fail}

- **Provision Failed During Configuration**  
  *The configuration process has failed.*  
  **Status**: `failed`  
  **Details**: The provisioning failed during the configuration phase.

- **Orchestrator Image Download Failed**  
  *The orchestrator image download has failed.*  
  **Status**: `failed`  
  **Details**: The orchestrator image download encountered an issue.

- **Orchestrator VM Creation Failed**  
  *The orchestrator VM creation process failed.*  
  **Status**: `failed`  
  **Details**: The VM could not be created successfully.

- **VM Critical Status**  
  *The VM is in a critical state after creation.*  
  **Status**: `failed`  
  **Details**: The VM has been created but is not functioning properly.

- **Instance Not Found**  
  *The specified instance was not found.*  
  **Status**: `not_found`  
  **Details**: The instance ID does not exist.

By following these statuses, you can efficiently monitor the progress of your VM creation and ensure that it aligns with your deployment objectives.
