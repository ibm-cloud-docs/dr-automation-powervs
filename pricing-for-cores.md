---
copyright:
  years: 2025
lastupdated: "2025-01-31"

subcollection: dr-automation

keywords: price core

---

# Pricing for IBM DR automation for PowerVS
{: #price}

DR Automation for PowerVS is available in select regions with scale-out logical partitions (LPAR). The systems supporting DR Automation have theoretical maximums for memory and processors, varying by server model and data center resources.
{:shortdesc: .shortdesc}


| Power Systems         | Processors | Memory            |
|-----------------------|------------|-------------------|
| E980 (9080-M9S)       | 143        | Up to 15,307 GB  |
| S922 (9009-22A)       | 15         | Up to 942 GB     |
| E1080 (9080-HEX)      | 240        | Up to 64 TB      |
{: caption="Theoretical maximum memory" caption-side="bottom"}

> **Notes:**
    Memory Limits by Data Center: In certain data centers, such as **DAL12, DAL13, OSA21, SAO01, TOK04, WDC04, and WDC06, E980** systems can support up to 23,070 GB of memory.
    Operating System Constraints: For IBM i, the **S922** and **S1022** machine types support a maximum of 4 cores per VM.



## Processor types
{: #procetype}

DR Automation for PowerVS uses a single, consistent pricing model across all processor types. Billing is based on the number of cores used, with the following processor options available:

- **S922**: Available in dedicated, shared uncapped, and shared capped configurations.
- **E980**: Provides high memory capacity options in dedicated, shared uncapped, and shared capped configurations.
- **S1022**: Designed for mid-range workloads, available in dedicated, shared uncapped, and shared capped configurations.
For information on different processor type functions, see [FAQ](/docs/dr-automation-powervs?topic=dr-automation-powervs-faqs).

All processor types are billed uniformly, regardless of configuration.

## All processors type pricing

| Number of cores | Hourly rate (Updated) | Monthly cost (730 hours) |
|----------------|----------------------|--------------------------|
| 1              | $0.06849              | $50.00                   |
| 2              | $0.13698              | $100.00                  |
| 3              | $0.20547              | $149.99                  |
| 4              | $0.27396              | $199.99                  |
| 5              | $0.34245              | $249.99                  |

{: caption="All processors type pricing" caption-side="bottom"}



  - **Uniform Rate** : All processor types, including dedicated, shared uncapped, and shared capped  configurations, are billed at the same hourly rate.

  - **Usage-Based Billing**: Costs are calculated on an hourly basis, and the monthly cost reflects usage for a full month (730 hours).

  - **Exclusions**: DR Automation billing excludes charges for operating systems, storage, and additional resources.


## End of billing
{: #eob}

The billing cycle for DR Automation for PowerVS ends when the Logical Partition (LPAR) is deleted. If you scale your infrastructure in response to workload demands, billing adjusts accordingly. **Stopping the LPAR alone does not end billing**; you must delete the LPAR to stop the billing cycle.

> **Important**:
Charges continue if the VM is suspended. To reduce costs for inactive VMs, use Dynamic Logical Partitioning (DLPAR) to resize to a minimal state, lowering core and memory usage.


## Pricing disclaimer
{: #pricedis}

This document provides a comprehensive overview of DR Automation pricing and usage for PowerVS, ensuring customers have accurate information for budgeting their DR solutions.

> **Important**:
Prices shown are for illustration only and may differ from actual billing. For precise estimates, use the IBM Cloud Cost Estimator. Final costs may vary based on discounts and promotions.
