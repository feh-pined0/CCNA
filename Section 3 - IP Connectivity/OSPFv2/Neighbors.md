OSPF enabled routers will try to form a neighbor relationship with another routers on the same network and area. The process occurs as follows:

- OSPF enabled interfaces will periodically send **OSPF Hello** messages (the interval is **10 seconds by default**);
	- These messages are sent to multicast address `224.0.0.5` (IPv4) or `FF02::05` (IPv6);
	- When a router is initially sending these hello messages, the interface is considered to be in the **Down** state (not line down, just Down to the OSPF process);
- If a router is connected to another router and both have OSPF enabled, the other router will listen to hello messages in order to get the neighbor's **Router ID**.
	- At this point, the second router's interface is in the **Init** state, while the first router is still in the **Down** state.
- The neighbor router will then send it's own hello messages.
	- Both routers then enter the **2-Way** state, where both are actively trying to form a neighbor relationship;
	- In this state, sometimes a process to define a **Designated Router** and **Backup Designated Router** will take place;
- Routers will then select a **Master** and **Slave** in this collision domain to start the LSA exchange;
	- This step is called **Exstart**, as in, EXchange start;
	- The router with the highest Router ID becomes the master, the other becomes the slave;
- The master router will send **Database Description** (DBD) packets. After receiving them, the slave will send it's own DBD packets;
	- These packets contain information about which LSAs each router have;
	- This step is called **Exchange**;
- After the exchange, routers will send **Link State Requests** (LSR) to request any LSAs they do not have;
	- These LSRs are responded to with **Link State Updates** (LSUs);
	- Then, the LSUs are responded to with LSAck;
	- This is called the **Loading** state;
- Finally, both routers enter the **Full** state. Timers begin decrementing.

Here is the summary of the process:

![[Pasted image 20231026162338.png]]
![[Pasted image 20231026162303.png]]

# Requirements

In order to become neighbors, routers must both meet a set of minimum requirements:

- The OSPF area must match on both interfaces;
- Interfaces must be on the same subnet/network;
- OSPF process must not be shutdown;
- Hello and Dead timers must match on both interfaces (these timers can be configured on each interface);
- OSPF authentication settings must match on both interfaces;

These last ones are not required, but OSPF may not function properly if not setup correctly:

- IP MTU (Maximum Transmit Unit) should match;
- OSPF Network type must match;