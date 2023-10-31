*Hot Standby Router Protocol* is a Cisco proprietary [[First Hop Redundancy Protocols|FHRP]] that has two versions: v1 and v2.

In HSRP:

- An **active** and **standby** router are elected.
- Routers communicate with each other using the multicast address:
	- `224.0.0.2` for v1 (the default multicast address for all routers);
	- `224.0.0.102` for v2
- Routers advertise a virtual MAC address for this VIP of:
	- `0000.0c07.acXX` for v1, where `XX` is the HSRP group number;
	- `0000.0c9f.fXXX` for v1, where `XXX` is the HSRP group number;

Each router can be active per subnet, making it possible to load-balance between different subnets.