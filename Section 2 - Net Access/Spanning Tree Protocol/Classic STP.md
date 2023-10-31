STP was originally created to address the problem of [[Broadcast Storms|broadcast storms]] in layer 2 networks. Today networks will use the more modern, [[PVST]] (*Per-VLAN Spanning Tree*), but the basics of STP apply to both protocols.

STP works by having layer 2 **bridge devices** (called bridge here for historic reasons, but in reality, when talking about STP, bridges mean [[Switches|switch]]) block some of it's ports, putting them in a "blocking state" and preventing them from forwarding any traffic that is not STP's.

The way STP chooses which ports get blocked is through a negotiation between all switches on the same broadcast domain. For this, STP periodically send out **BPDUs** (*Bridge Protocol Data Unit*).

The process of negotiation is as follows:

- For any STP instance, a **Root Bridge** (or Root Switch) needs to be elected. For this, switches broadcast their **Bridge ID** using BPDU frames.
> A Bridge ID consists of 16 bits (2 bytes): **4 priority bits** and **12 *Extended System ID* bits** (which is just the [[802.1Q Header|VID]] of the interface).
> ![[Pasted image 20230903185041.png]]

- Switches trade Bridge IDs and elect a Root Bridge based on which one has the lowest one;
	- In the case of a draw, the switch with the lowest MAC address wins;
	- The Root Bridge switch will have all it's ports on the [[Port States|forwarding state]];
- Each remaining switch selects **one** of it's interfaces to be the **Root Port**. This is the interface with the lowest [[Root Cost Calculation|Root Cost]].
	- The Root Port of each switch will be on a forwarding state.
- Finally, each layer 2 collision domain **should have one designated port**.
	- Each switch connected directly to the Root Bridge have the bridge interface as the root port of the switch;
	- Each switch connected to a end host has that interface as a designated port (as end hosts do not participate in STP);
	- Each switch connected to another switch in the Spanning Tree decide the designated port based on the lowest root cost between the two (**the lowest root cost of the switch, not the port being decided on**). If that is a tie between the two switches, the one with the lowest Bridge ID gets chosen and it's interface becomes designated, and the other one gets put **in a blocking state**.
		- Ports in a blocking state do not forward packets.

>**Review**:
> - SW1 gets elected the **Root Bridge** because it has the lowest **Bridge ID**.
> - SW2 and SW3's `G0/1` and `G0/0` become **Root Ports** because they have the lowest **Root Cost** to the Root Bridge.
> - SW2 and SW3 negotiate the designed port on the `SW2 G0/0` and `SW3 G0/1` collision domain.
> - Because SW2 has the lowest MAC address, it's `G0/0` port gets designated, and SW3's `G0/1` gets blocked.
>![[Pasted image 20230904142733.png]]