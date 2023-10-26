Some additional components of the routing table are mentioned in the official CCNA's study sheet:

- **Prefix**: it is the network part of an IP address. To check the prefix of an IP address:
	- Check the subnet mask. This can be in dotted notation (`255.255.255.0`) or [[CIDR]] (`/24`);
	- Separate all bits from the network and host parts of the IP;
		- For example, the `192.168.0.1/24` address has 24 bits for the prefix, so only `192.168.0` is part of the prefix, while `.1` is the host part;
	- Set all host bits to 0;
		- Using the example from before, `.1` becomes `.0`;
	- The result is the prefix: `192.168.0.0/24`.
- **Next-hop**: when routers forward packets, "next-hop" is the term that defines what is the next destination of the packet, be it an exit-interface on the same router, the IP address of another router, or both at the same time;