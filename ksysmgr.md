---
front_matter_title: "Ksysmgr commands"
lastupdated: "2024-10-23"
copyright: "2023, 2024"
subcollection: dr-automation
---
# Ksysmgr commands

The command provides a consistent interface to configure the controller system (KSYS) and to perform {{site.data.DR_full.attribute-definition-list}}operations by using a terminal or script.

```bash
ksysmgr [-v] [-f] [-l {low|max}] [-i] 
[-a {<ATTR#1>,<ATTR#2>,...}] <ACTION> <CLASS> [<NAME>]
[-h | <ATTR#1>=<VALUE#1> <ATTR#2>=<VALUE#2> ...]

ksysmgr [-v] [-f] [-l {low|max}] 
[-a {<ATTR#1>,<ATTR#2>,...}] <ACTION> <CLASS> [<NAME>]
<ATTR#1>=<VALUE#1> <ATTR#2>=<VALUE#2> ...]

         ACTION={add|modify|delete|query|manage|unmanage|...}\n\
         CLASS={ksyscluster|site|...}\n\

ksysmgr {-h|-?} [-v] [<ACTION> [<CLASS>]]

ksysmgr [-v] help
```
