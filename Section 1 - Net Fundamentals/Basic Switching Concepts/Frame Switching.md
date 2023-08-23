*Frame switching* is the most important concept for layer 2 forwarding and broadcast domains. Switches forward frames using only the layer 2 addresses (MAC addresses).

It consists on the following rules:

- A frame is received from a node on the switch interface;
- The switch checks for the frame's source MAC address on it's CAM table;
	- If an entry for this MAC does not exist, the switch creates one;
- The switch then checks for the destination MAC address on it's CAM table;
	- If an entry for this MAC exists, the switch forwards this frame to the interface the MAC is bound to;
	- If not, the switch floods all ports **except** the port the frame was received on;
- The destination device then receives the frame and responds to it using the same process, allowing the switch to learn it's MAC address too;

Bellow is an example of this process:

![[Switching-Logic-1.gif]]