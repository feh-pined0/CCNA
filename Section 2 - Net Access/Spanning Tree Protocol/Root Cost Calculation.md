When setting up STP topology, one of the most important steps for defining port roles is **Root Cost Calculation**. It is used to define which path is the best to use when forwarding frames to the [[Classic STP|Root Bridge]].

It works as follows:

- Each port gets assigned a **STP Cost** based on the maximum speed of the interface;
> The costs are the following:
> ![[Classic STP Interface Cost.png]]

- Each port that receives a BPDU from the Root Bridge adds the STP cost from it's **exit interface** to the Root Cost of the BPDU, and sends it to the other switches.
	- The Root Bridge advertises a cost of 0, because it already is the Root Bridge itself.
> Remember that, when a Root Bridge is elected, no switch sends BPDUs other than the elected Root Bridge. Switches only forward BPDUs that they receive.
> ![[Root Bridge & Ports Negotiation.png]]

- The switches then select the interface that has the lowest cost as the Root Port of the switch. In the previous example, SW2 would select it's `G0/0` as the root port, and SW3 would select `G0/0` too, because both have a cost of 4.

Also, there are some caveats to this calculation:

- If a switch receives two or more BPDUs with the same root cost, the port linking to the switch with the lowest **Bridge ID** gets elected as it's root port;
> Here, both SW4 and SW1 advertised root costs of 8, but SW1 has the lowest MAC address, so the link to SW1 gets elected as the root port.
> ![[Pasted image 20230903214159.png]]

- Similarly, if a switch has two links with another switch (and thus both the Bridge ID and MAC address would be the same, resulting in a draw), the link connected to the lowest remote **Port ID** would be elected the root port.
> Here, both links to SW1 have the same root cost, Bridge ID and MAC address, so the link to the remote switch's lowest Port ID (`G0/1` vs `G0/2`) gets elected.
> ![[Classic STP Root Port Redundant Selection.png]]

