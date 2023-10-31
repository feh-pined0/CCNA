*Gateway Load Balancing Protocol* is a Cisco proprietary [[First Hop Redundancy Protocols|FHRP]] that can **load balance within the same subnet** (a task that [[VRRP]] and [[HSRP]] cannot do).

In GLBP:

- An **AVG** (Active Virtual Gateway) is elected;
- Up to four **AVFs** (Active Virtual Forwarders) are assigned by the AVF (the AVG itself can be an AVF, too);
- Each AVF acts as the default gateway for a portion of the hosts in the subnet;
- Routers communicate with each other using the multicast address `224.0.0.102`;
- Routers advertise a virtual MAC address for this VIP of `0007.b400.xxyy` where:
	- `xx` is the GLBP group number;
	- `yy` is the AVF number;