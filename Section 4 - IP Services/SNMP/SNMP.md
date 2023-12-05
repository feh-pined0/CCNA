*Simple Network Management Protocol* is a set of tools (considered a framework) that helps in monitoring and maintaining a network by exchanging a series of messages between a server (the [[Network Management Station (NMS)|NMS]] - Network Management System or Station) and managed devices (such as routers, switches, printers, etc).

SNMP uses ports **UDP/162** and **UDP/161** for the NMS and managed device, respectively (using ephemeral ports when sending).

SNMP has many versions, but the most used and common ones are:

- **Version 1**: this is the first revision of the SNMP framework;
- **Version 2c**: this is a revision of version 2 that includes community string capabilities from version 1;
- **Version 3**: the most recent revision. Includes encryption and authentication support;

The SNMP framework works by storing data on a database called **MIB** (Management Information Base) and indexing this information using **OID**s (Object IDs). These OIDs are organized in a tree-like structure, generally beginning with the same numbers that denote the ISO standard being used, organization, etc.

Here is an example of a NMS -> Managed device structure:

![[SNMP Topology.png]]

>Here, each managed device runs an instance of the SNMP Agent - a software that interacts with the MIB and the SNMP Manager.
>The NMS runs the SNMP Manager, which queries information and receive updates from the SNMP Agents, and then displays it using an SNMP application, like [Solarwinds](https://www.solarwinds.com) for example.

