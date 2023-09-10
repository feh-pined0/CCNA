*Rapid Per-VLAN Spanning Tree* is faster version of STP, created for modern networks. [[Classic STP]] could take up to 50 seconds to react to changes in the topology, but Rapid PVST can take only a few seconds.

This is because RPVST **is not a timer based algorithm**, it reacts to changes in the topology using **bridge to bridge** handshakes.

Rapid PVST is very similar to regular STP, but the following differences apply:

## Root Cost Calculation

The Rapid PVST [[Root Cost Calculation|root cost calculation]] uses the following values:

![[Pasted image 20230910170810.png]]

## Port States

Instead of having five port states, Rapid PVST uses only three: **Discarding**, **Learning** and **Forwarding**.

> The discarding state combines the blocking, disabled and listening states into one:
> ![[Pasted image 20230910171108.png]]

## Port Roles

All port roles (Root Port and Designated Port) remain unchanged (both in the function they perform and the calculation used to decide the port role). However, **non-designated ports** are split into:

- **Alternate Port**: this port is in a **discarding state** and will take on the role of root port in case the current root port fails or loses connectivity to the root bridge;
- **Backup Port**: this port is also in a **discarding state**. It is assigned this role when a port receives a [[Superior BPDU|superior BPDU]] from another port on the same switch.

> Refer to this image as an example of a backup and alternate port (the device in the middle is a HUB):
> ![[Pasted image 20230910172209.png]]

Also, when the root port fails, the alternate port does not go through the learning state, it moves directly to the forwarding state. The switch also cleans the MAC address table of all the entries that came from the former root port (as those MAC addresses cannot be reached through that interface anymore). This function is called **UplinkFast**. It was present in classic STP and is built in Rapid PVST.

## Timers

Rapid PVST has much shorter timers than regular STP. Because of its many functions, an interface rarely has to wait timers to transition states, but when they do, the [[Timers|max age timer]] is reduced from **10 hello intervals** (a hello interval is still 2 seconds, so $2*10=20$ seconds) to **3 hello intervals** ($2*3=6$ seconds);

## Link Types

An additional concept is link types. There are three in total:

- **Edge**: an edge link type is an interface that is connected directly to an end host. It is similar to PortFast (and is configured the same way), i.e. the port moves directly to forwarding state;
- **Point-to-Point**: a connection made directly between two switches. It is automatically negotiated between the two devices;
- **Shared**: an interface that is connected to a [[Ethernet Shared Media and P2P|shared media]] (i.e. a HUB). It operates in half-duplex.
# Important notes

- In Rapid PVST, **all switches send their own BPDUs**, using timers from the root bridge (in classic STP, only the root bridged sent BPDUs);