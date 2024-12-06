---
front_matter_title: "Global Replication Service (GRS)"
lastupdated: "2024-10-23"
copyright: "2023, 2024"
subcollection: dr-automation
---
# Global Replication Service

The **Global Replication Service (GRS)** within IBM Power Virtual Server is essential for disaster recovery (DR), enabling asynchronous volume-level replication to ensure data resilience across locations during DR events.

## Key features

### 1. Storage and replication setup

GRS allows disaster recovery setup through asynchronous replication, using **Global Mirror Change Volume (GMCV)** technology. By replicating data volumes asynchronously, GRS ensures efficient data transfer between primary and secondary sites, maintaining data resilience in DR scenarios.

### 2. Volume group for consistency

GRS introduces a **volume group** concept, creating a consistency group to aggregate volumes for DR. This group includes volumes that must be recovered during a disaster, making them DR-capable. Adding volumes to the group streamlines replication processes across primary and backup sites.

### 3. Failover and failback support

GRS supports **failover and failback** operations, critical in DR scenarios. Through volume group management commands (`start` and `stop`), users can control replication flow during these operations. During failover, data volumes at the secondary site can be accessed and reactivated with minimal disruption, facilitating a smooth transition back to primary operations during recovery.

### 4. Resilience and networked location support

GRS currently supports predefined pairs of IBM Cloud data centers, allowing replication across mapped locations, such as **WDC04 to DAL13** (US East to US South) and **MAD02 to FRA04** (EU Madrid to Frankfurt), among others. IBM plans future expansions to increase geographical coverage, enabling broader DR support across PowerVS locations.

### 5. Automated resource management

By integrating GRS with IBM PowerVS infrastructure, **DR automation** leverages APIs to manage volume lifecycles, initiate replication, and control backup volume configurations. This automation minimizes manual intervention, enhancing the speed and reliability of DR responses.

## Summary

The integration of GRS into DR automation reinforces data consistency, operational continuity, and provides a solid foundation for automated disaster recovery across IBM Cloud locations.
