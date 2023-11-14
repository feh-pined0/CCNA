With ARP spoofing, an attacker can trick a device into "thinking" it has the correct IP -> MAC relation on it's table, while in reality the MAC address for the IP is replaced by the attacker's MAC. Then, while in the same broadcast domain, any packets sent from the targeted device to the spoofed device will actually go to the attacker's device, as shown in the figure below:

![[Pasted image 20231113155526.png]]

The spoofing occurs on the reply of the ARP request. The process is as follow:

- The target sends a ARP broadcast to search for SRV1 IP address;
	- As this is broadcast, any device in the same broadcast domain receives a copy of the frame, including attacker;
- SRV1 replies to this ARP with the IP -> MAC relation. This is a unicast frame.
- The attacker waits a while, and then sends another ARP reply to the target, rewriting the IP -> MAC relation on the target's ARP table;
- Then, any traffic sent from PC1 to SRV1 is directed to the attacker's MAC address;
- The attacker then can read, rewrite contents and forward to SRV1 and vice-versa;

