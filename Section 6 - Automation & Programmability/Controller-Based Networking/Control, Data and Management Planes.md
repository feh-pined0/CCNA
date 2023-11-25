A network has many aspects: the main one (of course) is forwarding packets. This is what provides connectivity between hosts. But besides that, inside a network there are many more things that need to happen in order for it to work properly.

For example, in layer 2, [[Classic STP|STP]] must be correctly configured in order to prevent broadcast storms and enable access for end hosts, [[Port Security|port security]] must be active in order to prevent unauthorized access. In layer 3, the correct [[Types of OSPF Routes|routing protocol]] should be configured to exchange routes between devices, ACLs should be configured to prevent undesirable traffic flows, and much more.

Theoretically, all of these network functions could be split into three different "planes": **Management**, **Control** and **Data**.

## Data Plane

The *Data Plane* wraps any networking device function that aims to forward and deliver user traffic/data between two hosts/devices. A concrete example of a data plane function would be any algorithm/program used by a router to make a forwarding decision. Things like **packet and datagram encapsulation**, **layer 2 ethernet header stripping and encapsulation** all are examples of data plane actions.

## Control Plane

The *Control Plane* wraps any resource that a networking device may have to control what is done by the data plane when forwarding traffic. These are the many tables and configurations a device has that can alter how/if traffic is forwarded through a device. For example, the **MAC address table** and the **routing table** belong in the control plane. Protocol operations like **OSPF**, **STP**, **ARP**, etc that have parameters that are evaluated when traffic needs to be forwarded are also all examples of control plane matter.

## Management Plane

The *Management Plane* wraps any resource that helps in the management of the control plane. This is the operation of protocols like [[SSH]], or features like console ports, [[Syslog|syslog]], [[SNMP]], [[NTP]], etc.