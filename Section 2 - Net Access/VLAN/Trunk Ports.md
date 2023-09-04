A *trunk switchport* is an interface that can carry data from multiple VLANs, while a normal [[Access Ports and Voice|access switchport]] can only forward data from one VLAN.

A trunk port can have a list of allowed VLANs to go through it's interface.

A trunk port also needs to be configured to use one method of encapsulation. This will almost always be [[802.1Q Header|802.1Q encapsulation]], as it is the industry standard, but there are some proprietary methods (but they are not used anymore).

Trunk ports are usually used in connections to routers and other network devices (such as a switch to switch uplink).