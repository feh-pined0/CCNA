*Dynamic Host Control Protocol* is one of the most important features of modern networks. It enables hosts to dynamically and automatically configure [[IP Parameters|IP parameters]], according to predefined values. It is a layer 7 (application) protocol.

DHCP works in a client-server fashion. The server provides **leases** to clients, which describes the IP parameters for the requesting client to use. These leases **may or may not expire depending on server configuration**.

DHCP uses **statically defined ports for the server and client**, that being **UDP/67** and **UDP/68**, respectively.

## The DHCP Lease Process

The main process of a DHCP lease provision is as follows:

- **DHCP Discover**: the client sends a discover packet in order to find the DHCP server on the LAN;
	- This datagram has source of `0.0.0.0` and destination of `255.255.255.255`, as the client does not know the server details yet, nor it's IP parameters;
	- Because of this, the frame also has source of the client's MAC address, and destination of `FFFF.FFFF.FFFF`;
	- In this message, the client can specify the **Bootp flags**, which define if the server response will be send unicast (`0x0000`) or broadcast (`0x8000`);
- **DHCP Offer**: the server responds the DHCP Discover by sending the client an available IP address, alongside with other configured **DHCP Options**, such as subnet mask, [[DNS|DNS servers]], lease times, etc;
	- Depending on the requested bootp flags on the DHCP Discover message, the server will respond with **datagram destination** `255.255.255.255` (for broadcast bootp flag) or the offered IP address (for unicast bootp flag);
	- This also applies for the **frame's destination**;
- **DHCP Request**: the client then requests the server to use the offered address, again specifying if the next server response should be unicast or broadcast;
	- This is a broadcast frame also, so destination IP is `255.255.255.255` and MAC `FFFF.FFFF.FFFF`;
- **DHCP Ack**: finally, the server acknowledges the IP usage by the client, reserving it for the time specified by the lease expiration time configured on the server;

Here is an example of this process:

![[Pasted image 20231103181538.png]]

