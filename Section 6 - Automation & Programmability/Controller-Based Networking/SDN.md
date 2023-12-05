*Software Defined Network* is an approach to networking and network management that:
>*...centralizes the [[Control, Data and Management Planes|control plane]] into an application called a controller*.

This means that, for any function that would be in the control plane of a device, in a SDN this function is partially or completely moved to a controller on the network. This is similar to [[Access Point Operation Mode|controller-based wireless management]], where the control and data planes of a [[Access Points|wireless access point]] are split between the actual access point (with the data plane) and a [[Controllers (WLC & Cisco DNA Center)|WLC]] (with the control plane).

For example, ACLs, routing tables, routing protocols, system information (such as syslog and environment variables) and **device configuration** are all centralized in a device that is charged with controlling the entire network.

For the "software" part of the network, these controllers and servers will then expose APIs that make it possible to configure and manage the devices connected to the controller through the usage of any compatible software (often the APIs used are so generic that even the final customer can write their own programs to work with the [[Network Automation Impacts|automation of the network]]).

To accomplish this, controllers use two groups of APIs: **Southbound** and **Northbound**.

## Southbound APIs

*Southbound APIs* are communication channels between the controller and the devices they control. These APIs are exposed on modern devices and provide two things: **information about the device** and **a means to configure it** (kind of like [[SNMP Message Types|SNMP Set messages]]).

![[Network Control Plane Centralization API.png]]

## Northbound APIs

*Northbound APIs* are communication channels between a **network-admin-facing application** (such as a control panel) **and the controller**. It is through this API that network admins can easily deploy network configurations, manage devices and gather information about the network (usually this is called a **single pane-of-glass**). More experienced professionals can develop their own applications to interact with this API, further increasing the degree of automation that the network has.

![[Network Controller NBI API.png]]

