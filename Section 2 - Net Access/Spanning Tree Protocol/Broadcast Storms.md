When designing networks, redundant links are mandatory. They ensure that the network uptime is at it's highest. But some problems rise from this premise, such as broadcast storms.

![[Broadcast Storm Example.png]]

Picture the following scenario: PC1 sends an ARP request for PC2's MAC address. SW1 forwards this broadcast frame to SW2 and SW3. SW2 forwards it to PC2 and SW3, who forwards it itself to PC3 and **SW2**. This last interaction creates a loop on the network, where SW2 and SW3 will keep forwarding this ARP request indefinitely.