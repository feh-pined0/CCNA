When using PVST+, [[Classic STP|STP]] runs one instance for each VLAN and, if not configured, will have the same topology of [[Port States|designated, root and blocked]] ports for each instance.

If there are multiple [[Default and Native VLANs|VLANs]] on the same topology, a technique can be used to block different ports on each STP instance to optimize the network traffic. This makes so that a port can be blocked on one VLAN, but forwarding on another, preventing what otherwise would be a completely disabled link.

For this, [[STP Toolkit|configuring the root bridges]] for each instance is all it takes.