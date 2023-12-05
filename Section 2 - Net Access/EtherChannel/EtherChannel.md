*EtherChannel* (also called *Port Channel* or *LAG* (*Link Aggregation Group*)) is a method (**not a protocol**) for grouping two or more physical interfaces in a single, logical interface.

This has many benefits:

- **More bandwidth**: EtherChannel load-balances traffic between the physical links, increasing the total bandwidth of the logical link;
- **Redundancy**: in case one or more links fail, the others can continue to operate normally, creating redundancy;
- **STP**: using EtherChannel it is possible to remove blocked ports on the [[STP]] topology, as multiple links are treated as a single, logical link;

EtherChannel is denoted in network diagrams as a circle, encapsulating the physical links:

![[Etherchannel Topology.png]]

Additional notes:

- When configuring EtherChannel on Cisco devices, a **Stand-Alone** physical interface is a port that is configured to be part of a bundle (group channel) but is **not** in a bundled state (not included in the channel group). This means that, although it is **configured** to that group channel, it is not bundled and thus is behaving like a standard, standalone port (forwarding STP traffic like it is just another port on the switch).